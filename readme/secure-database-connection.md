---
description: Add and extra layer of security to the database connection.
---

# Secure Database Connection

The DAP client library supports secure connections to databases using SSL/TLS. You can specify the SSL mode by using the `ssl` parameter in the connection string.&#x20;

### Supported SSL modes

* **`disable`**: SSL is disabled.
* **`prefer`** (default): Attempts an SSL connection first; falls back to a non-SSL connection if SSL fails.
* **`allow`**: Attempts a non-SSL connection first; retries with SSL if the first attempt fails.
* **`require`**: Forces an SSL connection, but certificate verification errors are ignored.
* **`verify-ca`**: Forces an SSL connection and verifies that the server certificate is issued by a trusted certificate authority (CA).
* **`verify-full`**: Forces an SSL connection, verifies that the server certificate is issued by a trusted CA, and ensures the server's hostname matches the certificate.

### Examples

1.  **Default SSL mode (prefer)**:

    ```bash
    postgresql://scott:password@server.example.com:5432/testdb
    ```
2.  **Forcing SSL connection**:

    ```bash
    postgresql://scott:password@server.example.com:5432/testdb?ssl=require
    ```
3.  **Forcing SSL connection and verifying the server certificate**:

    ```bash
    postgresql://scott:password@server.example.com:5432/testdb?ssl=verify-full
    ```

### Important Notes

**`verify-ca`** and **`verify-full`** modes require the CA certificate to be installed on your system to verify the server certificate. If the CA certificate is not installed, the connection will fail.

The location of CA certificates depends on the operating system:

* **Linux**: CA certificates are typically stored in `/etc/ssl/certs/` or similar directories.
* **Windows**: CA certificates are managed in the Windows Certificate Store.
* **macOS**: CA certificates are stored in the Keychain.
