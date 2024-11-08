# Data Formats

## Text (TSV) <a href="#text-tsv" id="text-tsv"></a>

Text format is a simple tabular format in which each record (table row) occupies a single line.

* Output always begins with a header row, which lists all metadata and data field names.
* Fields (table columns) are delimited by _tab_ characters.
* Non-printable characters and special values are escaped with _backslash_ (`\`), as shown below:

| Escape | Interpretation               |
| ------ | ---------------------------- |
|        | NULL value                   |
| `\b`   | Backspace (ASCII 8)          |
| `\f`   | Form feed (ASCII 12)         |
|        | Newline (ASCII 10)           |
|        | Carriage return (ASCII 13)   |
|        | Tab (ASCII 9)                |
| `\v`   | Vertical tab (ASCII 11)      |
| `\\`   | Backslash (single character) |

This format allows data to be easily imported into a database engine, e.g. with PostgreSQL [COPY](https://www.postgresql.org/docs/current/sql-copy.html).

Output in this format is transmitted as media type `text/plain` in UTF-8 encoding.

## Comma-separated values (CSV) <a href="#comma-separated-values-csv" id="comma-separated-values-csv"></a>

Comma-separated values (CSV) output follows [RFC 4180](https://www.ietf.org/rfc/rfc4180.html) with a few extensions:

* Output always begins with a header row, which lists all metadata and data field names.
* Strings are quoted with double quotes (`"`) if they contain special characters such as the double quote itself, the comma delimiter, a newline, a carriage return, a tab character, etc.
* Empty strings are always represented as `""` to avoid ambiguity with missing values.
* Missing values (a.k.a. `NULL`) are represented with no data (no characters between delimiters).
* Each row has the same number of fields.

These extensions allow differentiating empty strings (`""`) from missing values (a.k.a. `NULL`, represented as no data), for which RFC 4180 defines no rules. If a field is missing, the comma separators are still included, i.e. multiple comma separators may follow one another in a row if there is no data in subsequent fields.

Double quotes act as escape sequences inside a quoted string. If there are two consecutive double quote characters (i.e. `""`), the sequence is interpreted as a single double quote character (`"`). If a string contains newline or carriage return characters, they are emitted verbatim (in compliance with RFC 4180). As such, a record may be broken into several lines if the data contains newlines. (Some applications might not interpret these flawlessly, double-check your integration when you deal with CSV files.)

The following example demonstrates some of the above:

```csv
meta.action,key.pkey,value.prop1,value.prop2
U,1,a string,42
U,2,"a string, but in ""quotes"".",
D,3,,
U,4,"a multi-line
string",
```

Output in this format is transmitted as media type `text/csv` in UTF-8 encoding.

## JSON Lines <a href="#json-lines" id="json-lines"></a>

When the output data is represented in the [JSON Lines](https://jsonlines.org/) format, each record (table row) occupies a single line. Each line is a JSON object, which can be validated against the JSON schema returned by DAP API.

Output in this format is transmitted as media type `application/jsonlines` in UTF-8 encoding.

## Metadata

Output of DAP API may include record-level metadata in addition to table data.

In tabular formats (such as text and CSV), metadata are included in the output as additional columns. Consider the following example:

```csv
meta.action,key.pkey,value.prop1,value.prop2
U,1,"value1",42
U,2,"value2",NULL
D,3,,
```

This CSV output has a metadata section (`meta`), a primary key section (`key`) and a record value section (`value`). The metadata section contains a single field called `action`. The key and value sections comprise of several fields: `pkey`, `prop1` and `prop2`.

In the JSON Lines format, metadata, key and value sections are top-level properties `meta`, `key` and `value`, and have properties of their own:

```json
{ "meta": { "action": "U", ... }, "key": { "pkey": 1 }, "value": { "prop1": "value1", "prop2": 42 } }
{ "meta": { "action": "U", ... }, "key": { "pkey": 2 }, "value": { "prop1": "value2", "prop2": null } }
{ "meta": { "action": "D", ... }, "key": { "pkey": 3 } }
```

The set of metadata fields returned depends on the context. Some contexts may produce fields that other contexts do not. If output would contain no metadata fields, the section is omitted entirely.

### Action <a href="#action" id="action"></a>

The metadata field `action` identifies whether a record is _upserted_ (inserted or updated) or _(hard) deleted_ for an incremental query. In the result of a snapshot query, all records are to be understood as upserted.

* Upserted records (denoted by `U`) have all fields present in the data.
* Deleted records (denoted by `D`) only have the primary key field in their data, other field values are missing.

Occasionally, the term _soft delete_ is used, which in this context is equivalent to an update, and is denoted with a `U`, and all field values are included in the output.

### Timestamp <a href="#timestamp" id="timestamp"></a>

The metadata field `ts` indicates when a record was last updated in the underlying transactional data lake table. For an incremental query with `since` and `until` timestamp parameters, `ts` for all returned records is always strictly greater than `since`, and always less than or equal to `until`.

The timestamp may correlate to but does not correspond to the real time when the event took place (e.g. when a student enrolled to a course). If you need to know when the event happened, use the timestamp embedded in the data. Specifically, many tables have timestamp data columns such as `created_at` or `updated_at`, which are controlled by the product or application that generates the event (e.g. Canvas).

Timestamps are stored in fields of JSON type `string`, are formatted as per ISO-8601, and are to be understood as in time zone UTC. This is aligned with how timestamps are represented in the OpenAPI format `date-time` as per [RFC 3339](https://xml2rfc.tools.ietf.org/public/rfc/html/rfc3339.html#anchor14).

## Format transformations

Tabular data formats such as CSV cannot capture the hierarchy that JSON can represent easily. Nested JSON objects are flattened before they are included in the output. For example, consider the JSON data:

```json
{
    "id": 1,
    "question": {
        "headline": "title",
        "text": "some text"
    },
    "answers": [
        { "answer": "A", "score": 0 },
        { "answer": "B", "score": 1 },
        { "answer": "C", "score": 0 }
    ]
}
```

Here, the property `question` with two fixed sub-properties can be flattened into CSV columns `question.headline` and `question.text`. However, the property `answers` cannot be flattened because the list has an indeterminate cardinality. Items with indeterminate cardinality are transmitted as a JSON string. (Cardinality check is performed on the data (JSON) schema, not the actual data.)

This is how text output would look like after flattening (tabs are shown as four spaces):

```
data.id    data.question.headline    data.question.text    data.answers
1    title    some text    [{"answer":"A","score":0},{"answer":"B","score":1},{"answer":"C","score":0}]
```

In a similar fashion, this is how CSV output would look after flattening:

```csv
data.id,data.question.headline,data.question.text,data.answers
1,title,some text,"[{""answer"":""A"",""score"":0},{""answer"":""B"",""score"":1},{""answer"":""C"",""score"":0}]"
```

If you wish to avoid format transformations entirely, use the JSON Lines data format.
