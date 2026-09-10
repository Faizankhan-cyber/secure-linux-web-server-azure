# Troubleshooting

## Problem 1

SSH connection failed.

### Cause

Private key permissions were too open.

### Solution

Restricted the SSH private key permissions using:

```powershell
icacls vm-web-01_key.pem /inheritance:r
```

---

## Problem 2

Website was not accessible from the browser.

### Cause

HTTP port (80) was not allowed through the Network Security Group.

### Solution

Created an inbound rule allowing TCP port 80.

---

## Problem 3

Website still timed out after opening port 80.

### Cause

Used HTTPS instead of HTTP.

### Solution

Accessed:

http://<Public-IP>

instead of

https://<Public-IP>

---

## Problem 4

Could not upload website.

### Cause

Incorrect SCP command and wrong key location.

### Solution

Uploaded the file successfully using SCP.

---

## Problem 5

Git push failed.

### Cause

Repository history differed after uploading files directly through GitHub.

### Solution

Cloned the repository again and continued development from a single local copy.