# Lab 4: Code Translation - Python to JavaScript with Bob

## Overview

In this lab, you'll learn how to use Bob to translate code from one programming language to another while maintaining functionality and applying language-specific best practices.

You will translate a Python data processing script into an equivalent JavaScript implementation using Node.js.

This reflects a common real-world scenario where teams need to modernize applications, migrate codebases, or translate existing logic into a different technology stack.

> 🧠 **Bob Differentiator: Intelligent Resource Optimization**  
> During this lab, Bob will automatically select the right AI model for each translation task. Complex language feature mappings use powerful models for accuracy, while simple syntax conversions use lighter models for speed.
>
> This automatic model selection happens transparently, optimizing both quality and cost.

## What You'll Translate

You will translate a Python data processing script into JavaScript using Node.js.

The Python script:
- Reads CSV files
- Performs statistical calculations
- Exports results to JSON

The final goal is to create an equivalent JavaScript implementation that preserves the same functionality.

## What You'll Learn

By the end of this lab, you will:
- ✅ Use Ask Mode to analyze source code
- ✅ Use Plan Mode to plan a translation strategy
- ✅ Use Code Mode to implement the translation
- ✅ Understand language-specific patterns
- ✅ Map Python features to JavaScript equivalents
- ✅ Maintain code functionality across languages
- ✅ Apply best practices in both languages

## Prerequisites

Before starting, make sure you have:
- [ ] IBM Bob access
- [ ] Python 3.8+
- [ ] Node.js 14+
- [ ] A local workspace for Bob

Helpful but not required:
- [ ] Completion of Lab 1
- [ ] Basic familiarity with Python and JavaScript

## Lab Structure

- [Analyze the existing Python code](#step-1-analyze-the-existing-python-code)
- [Plan the translation strategy](#step-2-plan-the-translation-strategy)
- [Implement the translation with Code Mode](#step-3-implement-the-translation-with-code-mode)
- [Verify and compare both versions](#step-4-verify-and-compare-both-versions)
- [Appendix](#appendix)

---

# Step 1: Analyze the existing Python code

## 1.1: Review the Python code

Before translating code, it is important to understand what the original code does.

Open the Python data processor file:

```text
bob-labs/lab3/source/data_processor.py
```

Review the code structure and pay attention to the following elements:
- Class-based design
- Type hints, such as `: str` and `-> Dict`
- Context managers, such as `with open()`
- List comprehensions
- Dictionary operations
- CSV and JSON handling

**✅ Checkpoint**: You have opened and reviewed the Python source file.

---

## 1.2: Switch to Ask Mode

Open Bob and switch to **Ask Mode**.

Ask Mode is useful when you want Bob to explain, analyze, or reason about code without modifying files.

---

## 1.3: Understand the code structure

Ask Bob:

```text
Analyze the Python code in bob-labs/lab3/source/data_processor.py and explain:
1. What is the overall purpose of this code?
2. What are the main components and their responsibilities?
3. What Python-specific features are being used?
4. What are the key data structures and algorithms?
```

Bob should explain:
- **Purpose**: The script processes CSV data and generates statistical summaries
- **Main components**:
  - `DataProcessor` class
  - Methods for loading, analyzing, and exporting data
  - File input/output operations
  - Statistical calculations
- **Python-specific features**:
  - Type hints for better code documentation
  - Context managers for safe file handling
  - List comprehensions for concise data processing
  - Dictionary operations
- **Data structures**:
  - Lists
  - Dictionaries
  - CSV rows

**✅ Checkpoint**: You understand the purpose and structure of the Python code.

---

## 1.4: Identify translation challenges

Still in **Ask Mode**, ask Bob:

```text
What challenges might we face when translating this Python code to JavaScript?
Consider:
- Language syntax differences
- Built-in library differences
- Async/sync patterns
- Type system differences
```

Bob should identify challenges such as:

1. **File I/O**  
   Python uses `with open()`, while Node.js commonly uses asynchronous file operations or streams.

2. **CSV parsing**  
   Python has a built-in `csv` module, while JavaScript usually relies on npm packages such as `csv-parser`.

3. **Type hints**  
   Python type hints can be mapped to JSDoc comments or TypeScript-style documentation.

4. **List comprehensions**  
   Python list comprehensions need to be translated into JavaScript array methods such as `map()`, `filter()`, and `reduce()`.

5. **Synchronous vs asynchronous patterns**  
   Python code is often synchronous by default, while Node.js commonly uses asynchronous patterns.

**✅ Checkpoint**: You understand the main translation challenges before implementation.

---

# Step 2: Plan the translation strategy

Now that you understand the Python source code, the next step is to create a clear translation plan.

This helps avoid directly jumping into code generation without understanding the design decisions.

## 2.1: Switch to Plan Mode

Change from **Ask Mode** to **Plan Mode**.

> 💡 **Key Learning**  
> Plan Mode helps create a clear roadmap before coding. This is especially useful when translating code between languages because the goal is not only to convert syntax, but also to preserve functionality and apply the right patterns in the target language.

---

## 2.2: Create a translation mapping

Ask Bob:

```text
Create a detailed translation plan for converting the Python data processor to JavaScript.
Include:
1. Feature-by-feature mapping (Python → JavaScript)
2. Library/module equivalents
3. Syntax transformations needed
4. Recommended JavaScript patterns
5. File structure for the JavaScript version
```

Bob should produce a mapping similar to this:

| Python Feature | JavaScript Equivalent | Notes |
|---|---|---|
| `class DataProcessor` | `class DataProcessor` | Classes work similarly |
| `def __init__(self, filename: str)` | `constructor(filename)` | Constructor syntax differs |
| `with open(file)` | `fs.promises.readFile()` or streams | JavaScript file handling is usually asynchronous |
| `csv.DictReader` | `csv-parser` library | Requires an npm package |
| List comprehension | `Array.map()`, `Array.filter()` | JavaScript uses array methods |
| `sum(values)` | `values.reduce()` | JavaScript uses `reduce()` for aggregation |
| `min()` / `max()` | `Math.min()` / `Math.max()` | Requires spreading the array |
| Type hints | JSDoc comments | Optional but recommended |
| `if __name__ == '__main__'` | `if (require.main === module)` | Node.js uses a different main execution pattern |

**✅ Checkpoint**: You have a clear Python-to-JavaScript translation mapping.

---

## 2.3: Plan the module structure

Ask Bob:

```text
Design the JavaScript module structure for the translated code.
Should we use:
- ES6 modules or CommonJS?
- Classes or functional approach?
- Async/await or promises?
- Any additional error handling?
```

A recommended structure is:

```javascript
// Use CommonJS for Node.js compatibility
// Use ES6 class syntax because it maps clearly to the Python class
// Use async/await for cleaner asynchronous code
// Add error handling with try/catch
// Include JSDoc comments for type documentation
```

For this lab, the JavaScript version should:
- Use CommonJS with `require()` and `module.exports`
- Use an ES6 class
- Use async/await where appropriate
- Include clear error handling
- Include JSDoc comments for documentation

**✅ Checkpoint**: You understand the target JavaScript structure.

---

## 2.4: Identify dependencies

Ask Bob:

```text
What npm packages will we need for the JavaScript version?
List the packages and their purposes.
```

Required packages:

| Package | Purpose |
|---|---|
| `csv-parser` | Parses CSV files in Node.js |
| `fs` | Built-in Node.js module for file operations |

No additional packages are required for this lab.

> 💡 **Context Management**  
> As you work through this translation, Bob uses dynamic context window compression to efficiently manage both the Python source code and JavaScript target code in memory.
>
> This allows Bob to maintain full context of both codebases while minimizing token usage and costs.

**✅ Checkpoint**: You know which dependencies are needed for the JavaScript implementation.

---

# Step 3: Implement the translation with Code Mode

Now that the translation has been analyzed and planned, you can use Bob to implement the JavaScript version.

## 3.1: Switch to Code Mode

Change to **Code Mode**.

Unlike Ask Mode or Plan Mode, Code Mode can:
- Create files
- Modify code
- Refactor existing logic
- Implement full solutions
- Generate and update project files

---

## 3.2: Create the package configuration

Ask Bob:

```text
Create a package.json file for the JavaScript data processor with:
- Name: data-processor
- Version: 1.0.0
- Dependencies: csv-parser
- Main entry point: data_processor.js
- Scripts for running the processor
```

Bob should create a `package.json` file similar to this:

```json
{
  "name": "data-processor",
  "version": "1.0.0",
  "description": "JavaScript translation of a Python CSV data processor",
  "main": "data_processor.js",
  "scripts": {
    "start": "node data_processor.js"
  },
  "dependencies": {
    "csv-parser": "^3.0.0"
  }
}
```

**✅ Checkpoint**: The JavaScript project configuration has been created.

---

## 3.3: Translate the complete class

Ask Bob:

```text
Translate the entire DataProcessor class from Python to JavaScript.
Include:
- Constructor matching Python's __init__
- All methods with equivalent functionality
- JSDoc comments for type documentation
- Async/await for file operations
- Error handling
- Main execution logic
```

Bob should translate the entire class structure and create a complete JavaScript implementation.

The result should include a structure similar to this:

```javascript
/**
 * DataProcessor - Analyzes CSV files and generates statistics.
 * Translated from Python to JavaScript.
 */

const fs = require('fs').promises;
const { createReadStream } = require('fs');
const csv = require('csv-parser');

class DataProcessor {
    constructor(filename) {
        // ...
    }

    async loadData() {
        // ...
    }

    calculateStatistics() {
        // ...
    }

    async exportResults(outputFile) {
        // ...
    }
}

// Main execution logic
if (require.main === module) {
    // ...
}

module.exports = DataProcessor;
```

Bob will translate all relevant components in one go, including:
- Constructor
- Data loading method
- Statistical calculation method
- JSON export method
- Main execution logic
- Module exports

**✅ Checkpoint**: The JavaScript version of the class has been generated.

---

## 3.4: Understand the file I/O translation

After Bob generates the JavaScript implementation, switch back to **Ask Mode** to understand the translation decisions.

Ask Bob:

```text
Explain how you translated the load_data method from Python to JavaScript.
What are the key differences between Python's context manager and JavaScript's stream-based approach?
```

Bob should explain the difference between Python's context manager approach and JavaScript's stream-based approach.

Python original:

```python
def load_data(self) -> None:
    with open(self.filename, 'r') as file:
        reader = csv.DictReader(file)
        self.data = [row for row in reader]
```

JavaScript translation:

```javascript
async loadData() {
    return new Promise((resolve, reject) => {
        const results = [];

        createReadStream(this.filename)
            .pipe(csv())
            .on('data', (row) => results.push(row))
            .on('end', () => {
                this.data = results;
                resolve();
            })
            .on('error', reject);
    });
}
```

Key points:
- Python uses `with open()` to safely open and close files.
- JavaScript uses streams to process file data asynchronously.
- The `csv-parser` package reads rows from the file stream.
- A Promise is used so the method can be awaited.

**✅ Checkpoint**: You understand how file loading was translated.

---

## 3.5: Understand the statistical calculations translation

Ask Bob:

```text
Explain how you translated the calculate_statistics method.
How did you convert Python's list comprehensions and built-in functions to JavaScript?
```

Python original:

```python
def calculate_statistics(self) -> Dict:
    numeric_fields = [k for k in self.data[0].keys()
                     if self.data[0][k].replace('.', '').isdigit()]

    values = [float(row[field]) for row in self.data]

    stats[field] = {
        'mean': sum(values) / len(values),
        'min': min(values),
        'max': max(values)
    }
```

JavaScript translation:

```javascript
calculateStatistics() {
    const numericFields = Object.keys(this.data[0])
        .filter(key => !isNaN(parseFloat(this.data[0][key])));

    const values = this.data.map(row => parseFloat(row[field]));

    stats[field] = {
        mean: values.reduce((a, b) => a + b, 0) / values.length,
        min: Math.min(...values),
        max: Math.max(...values)
    };
}
```

Key points:
- Python list comprehensions become JavaScript array methods.
- `sum(values)` becomes `values.reduce()`.
- `min(values)` becomes `Math.min(...values)`.
- `max(values)` becomes `Math.max(...values)`.
- Python dictionaries become JavaScript objects.

**✅ Checkpoint**: You understand how the statistical logic was translated.

---

## 3.6: Understand the JSON export translation

Ask Bob:

```text
Explain how you translated the export_results method.
What's the difference between Python's synchronous file writing and JavaScript's async approach?
```

Bob should explain that:
- Python can write JSON synchronously using `json.dump()`.
- JavaScript can use `fs.promises.writeFile()` for asynchronous writing.
- `JSON.stringify()` converts JavaScript objects into formatted JSON.
- `await` ensures the file is written before continuing.

Example JavaScript pattern:

```javascript
async exportResults(outputFile) {
    const statistics = this.calculateStatistics();
    await fs.writeFile(outputFile, JSON.stringify(statistics, null, 2));
}
```

**✅ Checkpoint**: You understand how JSON export was translated.

---

## 3.7: Understand the main execution logic

Ask Bob:

```text
Explain how you translated Python's if __name__ == '__main__' pattern to JavaScript.
Why did you use an async IIFE (Immediately Invoked Function Expression)?
```

JavaScript translation:

```javascript
// Main execution
if (require.main === module) {
    (async () => {
        try {
            const processor = new DataProcessor('data.csv');
            await processor.loadData();
            await processor.exportResults('statistics.json');
            console.log('✅ Processing complete!');
        } catch (error) {
            console.error('❌ Error:', error.message);
            process.exit(1);
        }
    })();
}

module.exports = DataProcessor;
```

Bob should explain that:
- `require.main === module` checks whether the file is being executed directly.
- This is the Node.js equivalent of Python's `if __name__ == '__main__'`.
- The async IIFE allows the script to use `await` at the top level.
- `try/catch` handles runtime errors clearly.

> 💡 **Key Learning**  
> Code Mode handles the actual translation while maintaining functionality. Ask Mode can then be used again to understand the reasoning behind the generated code.

**✅ Checkpoint**: You understand how the execution logic was translated.

---

# Step 4: Verify and compare both versions

The final step is to test both versions and compare the output.

## 4.1: Create sample data

Create a sample CSV file for testing.

Create a file named:

```text
data.csv
```

Add the following content:

```csv
name,age,score,grade
Alice,25,95.5,A
Bob,30,87.3,B
Charlie,22,92.1,A
Diana,28,88.7,B
```

**✅ Checkpoint**: The sample CSV file has been created.

---

## 4.2: Run the Python version

Run the Python version from the source folder:

```bash
cd wxo_bob_workshop_portugal/bob-labs/lab4/source
python data_processor.py
```

Expected output:

```text
Processing complete!
Results saved to statistics.json
```

Expected `statistics.json` output:

```json
{
  "age": {
    "mean": 26.25,
    "min": 22,
    "max": 30,
    "count": 4
  },
  "score": {
    "mean": 90.9,
    "min": 87.3,
    "max": 95.5,
    "count": 4
  }
}
```

**✅ Checkpoint**: The Python version runs successfully.

---

## 4.3: Run the JavaScript version

> **Note**  
> This repository includes a reference JavaScript translation in:
>
> ```text
> bob-labs/lab4/solution/
> ```
>
> If Bob generated the files in a different location in your own workspace, adapt the commands accordingly.

Navigate to the JavaScript solution directory:

```bash
cd wxo_bob_workshop_portugal/bob-labs/lab4/solution
npm install
node data_processor.js
```

Expected output:

```text
✅ Processing complete!
Results saved to statistics.json
```

**✅ Checkpoint**: The JavaScript version runs successfully.

---

## 4.4: Compare both implementations

Switch back to **Ask Mode** and ask Bob:

```text
Compare the Python and JavaScript implementations.
What are the key differences in:
1. Code structure
2. Syntax
3. Async handling
4. Error handling
5. Performance characteristics
```

Bob should compare:
- How Python and JavaScript structure classes and methods
- How each language handles file operations
- How synchronous and asynchronous execution differ
- How errors are handled
- How data transformations are written in each language

---

## 4.5: Verify functionality

Both versions should produce equivalent results:
- ✅ Same statistical calculations
- ✅ Same JSON structure
- ✅ Same file handling behavior
- ✅ Equivalent error handling

**✅ Checkpoint**: The translated JavaScript version preserves the functionality of the original Python version.

---

# Congratulations 🎉 You’ve completed Lab 4!

You’ve successfully learned how to:
- ✅ Analyze code structure across languages
- ✅ Plan translation strategies systematically
- ✅ Map language-specific features
- ✅ Implement translations while maintaining functionality
- ✅ Handle async/sync differences
- ✅ Apply best practices in both languages
- ✅ Verify translated code correctness

> 🎯 **Intelligent Optimization in Action**  
> Throughout this lab, Bob's intelligent resource optimization was working behind the scenes. Bob automatically selected frontier-class models for complex translation decisions, such as mapping Python's context managers to JavaScript's async patterns, and lighter models for straightforward syntax conversions.
>
> This optimization can reduce AI costs while maintaining high-quality results.

---

# Appendix

## Translation Patterns Learned

### 1. Class translation

Python:

```python
class DataProcessor:
    def __init__(self, filename: str):
        self.filename = filename
```

JavaScript:

```javascript
class DataProcessor {
    constructor(filename) {
        this.filename = filename;
    }
}
```

---

### 2. List comprehensions to array methods

Python:

```python
values = [float(row[field]) for row in self.data]
```

JavaScript:

```javascript
const values = this.data.map(row => parseFloat(row[field]));
```

---

### 3. File I/O

Python:

```python
with open(filename, 'r') as file:
    data = file.read()
```

JavaScript:

```javascript
const data = await fs.promises.readFile(filename, 'utf8');
```

---

### 4. Type hints to JSDoc

Python:

```python
def calculate_statistics(self) -> Dict:
    pass
```

JavaScript:

```javascript
/**
 * @returns {Object} Statistics object
 */
calculateStatistics() {
    // ...
}
```

---

## Best Practices Applied

### Python best practices

- ✅ Type hints for clarity
- ✅ Context managers for safe resource handling
- ✅ List comprehensions for readability
- ✅ Docstrings for documentation
- ✅ PEP 8 style guide

### JavaScript best practices

- ✅ JSDoc for type documentation
- ✅ Async/await for asynchronous operations
- ✅ Promises for async patterns
- ✅ Error handling with try/catch
- ✅ Modern ES6+ syntax
- ✅ Module exports for reusability

---

## Common Translation Challenges

### Challenge 1: Synchronous vs asynchronous execution

**Problem**: Python's file operations are often synchronous, while JavaScript commonly uses asynchronous I/O.

**Solution**: Use async/await in JavaScript.

```javascript
async loadData() {
    await fs.promises.readFile(this.filename);
}
```

---

### Challenge 2: Built-in libraries

**Problem**: Python includes a rich standard library, while JavaScript often relies on npm packages.

**Solution**: Use npm packages when needed.

```bash
npm install csv-parser
```

---

### Challenge 3: List comprehensions

**Problem**: Python has concise list comprehensions, while JavaScript uses array methods.

**Solution**: Use `filter()`, `map()`, and `reduce()`.

```javascript
numbers
    .filter(x => x > 0)
    .map(x => x * 2);
```

---

### Challenge 4: Type safety

**Problem**: Python supports optional type hints, while JavaScript is dynamically typed.

**Solution**: Use JSDoc or TypeScript-style documentation.

```javascript
/**
 * @param {string} filename
 * @returns {Promise<void>}
 */
async loadData(filename) {
    // ...
}
```
