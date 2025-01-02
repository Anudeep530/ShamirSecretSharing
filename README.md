
# Shamir's Secret Sharing - Polynomial Interpolation

This project implements a simplified version of Shamir's Secret Sharing algorithm using polynomial interpolation to find the constant term (`c`) of a polynomial from encoded roots. The solution works with JSON test cases that provide roots in various bases.

---

## Features

- **Polynomial Interpolation**: Computes the polynomial's constant term (`c`) using Lagrange interpolation.
- **JSON Input Parsing**: Reads roots and their respective bases from JSON files.
- **Base Conversion**: Decodes values from different bases into integers.
- **256-Bit Arithmetic**: Handles large numbers using Java's `BigInteger` class.

---

## How It Works

1. **Input JSON**:
   - Contains `n` encoded roots and the minimum number of roots `k` required to reconstruct the polynomial.
   - Each root is represented by its key (x-value) and a value encoded in a specific base.

2. **Decoding**:
   - Decode the y-values (root values) from their respective bases into integers.

3. **Lagrange Interpolation**:
   - Uses the decoded points `(x, y)` to compute the constant term (`c`) of the polynomial.

4. **Output**:
   - Prints the reconstructed secret (constant term `c`) for each test case.

---

## Input Format

The input is a JSON file with the following structure:

```json
{
    "keys": {
        "n": <number of roots>,
        "k": <minimum roots required>
    },
    "1": {
        "base": <base of value>,
        "value": <encoded y-value>
    },
    ...
}
```

### Example:
```json
{
    "keys": {
        "n": 4,
        "k": 3
    },
    "1": {
        "base": "10",
        "value": "4"
    },
    "2": {
        "base": "2",
        "value": "111"
    },
    "3": {
        "base": "10",
        "value": "12"
    },
    "6": {
        "base": "4",
        "value": "213"
    }
}
```

---

## Prerequisites

- Java 8 or later
- Gradle (for build and dependency management)
- JSON Library (`org.json`) for parsing input files

---

## Setup

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Add Dependencies**:
   Add the following to your `build.gradle`:
   ```groovy
   dependencies {
       implementation 'org.json:json:20210307'
   }
   ```

3. **Prepare Input Files**:
   Place JSON test cases (e.g., `testcase1.json`, `testcase2.json`) in the project root or a specific directory.

---

## Running the Program

### With Gradle:
1. Build the project:
   ```bash
   ./gradlew build
   ```

2. Run the program:
   ```bash
   ./gradlew run
   ```

### Without Gradle:
1. Compile the program:
   ```bash
   javac -cp json-20210307.jar ShamirSecretAssignment.java
   ```

2. Run the program:
   ```bash
   java -cp .:json-20210307.jar ShamirSecretAssignment
   ```

---

## Example Output

For the provided example test cases:

```bash
Secret for Testcase 1: 1234
Secret for Testcase 2: 5678
```

---

## Troubleshooting

### Common Issues:
1. **File Not Found**:
   Ensure the JSON files (`testcase1.json`, `testcase2.json`) are in the correct directory.

2. **Missing Dependencies**:
   Ensure the `org.json` library is added to your `build.gradle` file.

3. **Large Numbers**:
   Verify that `BigInteger` is used for all large number computations.

4. **Malformed JSON**:
   Check the structure of your input files.

### Debugging Tips:
- Add debug logs to inspect parsed JSON, decoded values, and intermediate results in the interpolation process.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contributing

Feel free to submit issues, fork the repository, and send pull requests for improvements or bug fixes.

---
