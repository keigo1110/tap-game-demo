# GitHub Actions CI/CD Pipeline

This directory contains the CI/CD configuration for the Simple Tap Game project.

## Pipeline Overview

The CI pipeline (`ci.yml`) runs automatically on:

- Push to `main` or `develop` branches
- Pull requests targeting `main` branch

## Test Matrix

- **Node.js**: Version 20 (as specified in requirements)
- **OS**: Ubuntu Latest

## Validation Steps

### 1. HTML Structure Validation

- Verifies `index.html` exists and has proper HTML5 structure
- Checks for required game elements:
  - Score display (`id="score"`)
  - Game circle (`id="circle"`)
  - Game Over modal (`id="gameOverModal"`)

### 2. JavaScript Syntax Validation

- Extracts and validates JavaScript code from HTML
- Verifies syntax correctness
- Ensures all required functions exist:
  - `updateScore()`
  - `startTimer()`
  - `endGame()`
  - `restartGame()`

### 3. Line Count Constraint

- Enforces the 200-line limit as specified in requirements
- Current implementation: 187/200 lines

### 4. CSS Structure Validation

- Verifies presence of required CSS classes:
  - `.score`, `.circle`, `.modal`, `.modal-content`, `.restart-btn`
- Ensures blue circle background color is present

### 5. Game Functionality Checks

- Validates 10-second timer implementation (10000ms)
- Confirms "Game Over" text presence
- Verifies "Restart" button existence

### 6. Deployment Readiness (Main Branch Only)

- Checks for all required project files
- Validates HTML structure for static serving
- Confirms project is deployment-ready

## Local Testing

You can run similar validations locally using Node.js:

```bash
# Check JavaScript syntax
node -e "const fs = require('fs'); /* validation code */"

# Check HTML structure
grep -q 'id="score"' index.html && echo "✅ Score element found"

# Check line count
wc -l index.html
```

## CI Reports

The pipeline generates detailed test reports in the GitHub Actions summary, including:

- Test results overview
- Project statistics (lines, file size)
- Node.js version information
- Deployment status
