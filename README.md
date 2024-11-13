Here's a README for your script:

---

# Hash Cracker Script v3.0

This Python script is designed to attempt cracking various hash types (MD5, SHA1, SHA-256, SHA-384, SHA-512) by querying multiple online APIs and databases to retrieve the original string from a given hash. It supports the following methods for cracking:

- **Single hash cracking**: Cracking a single hash passed as an argument.
- **File cracking**: Cracking all hashes in a file and saving the results.
- **Directory cracking**: Searching for hashes within files in a directory and cracking them.

## Requirements

To use this script, you need to have the following dependencies installed:

- Python 3
- `requests` library
- `concurrent.futures` (included in Python standard library)
- `urllib3` (to disable SSL warnings)
  
You can install the required Python packages by running:

```bash
pip install requests urllib3
```

## Usage

### 1. Cracking a Single Hash

You can provide a single hash via the `-s` argument. The script will attempt to crack the hash using various APIs.

```bash
python3 hash_cracker.py -s <hash>
```

Example:
```bash
python3 hash_cracker.py -s aaf4c61ddcc5e8a2dabede0f3b482cd9aea9
```

### 2. Cracking Hashes from a File

To crack hashes stored in a file, provide the file using the `-f` argument. Each hash should be on a new line.

```bash
python3 hash_cracker.py -f <file_with_hashes>
```

Example:
```bash
python3 hash_cracker.py -f hashes.txt
```

### 3. Cracking Hashes in a Directory

To search for and crack hashes within a directory, use the `-d` argument. The script will search for hash patterns (`md5`, `sha1`, `sha256`, `sha384`, `sha512`) in files in the given directory.

```bash
python3 hash_cracker.py -d <directory_with_files>
```

Example:
```bash
python3 hash_cracker.py -d /home/user/hash_files/
```

### 4. Adjusting the Number of Threads

By default, the script uses 4 threads for parallel cracking. To specify a different number of threads, use the `-t` argument:

```bash
python3 hash_cracker.py -t 8 -f <file_with_hashes>
```

Example:
```bash
python3 hash_cracker.py -t 8 -f hashes.txt
```

### 5. Output

- **Single Hash Cracking**: Displays the cracked result directly in the terminal.
- **File/Directory Cracking**: Saves the results in a file named `cracked-<input_file>.txt`.

## Supported Hash Functions

- **MD5** (32 characters)
- **SHA1** (40 characters)
- **SHA-256** (64 characters)
- **SHA-384** (96 characters)
- **SHA-512** (128 characters)

## Customizing the Script

The script supports multiple API methods for cracking hashes, including:
- **`gamma`**: Nitrxgen MD5 database
- **`beta`**: HashToolkit
- **`theta`**: MD5Decrypt API

You can modify or add new API functions in the script to improve or extend hash cracking capabilities.

### Example Output

```bash
[+] Hash function : MD5
[~] Attempting to crack the hash aaf4c61ddcc5e8a2dabede0f3b482cd9aea9
aaf4c61ddcc5e8a2dabede0f3b482cd9aea9 : password
```

## Notes

- **Warning**: Some of the APIs used by the script may have rate limits or require registration for higher request limits. Consider using your own API keys or looking into local cracking tools like **Hashcat** if the APIs are insufficient.
- **Thread Pool**: The script utilizes Python's `concurrent.futures.ThreadPoolExecutor` to crack hashes in parallel, improving performance for cracking multiple hashes.
- **SSL Warnings**: SSL warnings are suppressed (`urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)`), as some APIs may not provide SSL certificates.

## License

This script is provided under the MIT License.

---

This README should provide all necessary information on how to use the script effectively, and also give insights on the customization options available. Let me know if you need further adjustments!
