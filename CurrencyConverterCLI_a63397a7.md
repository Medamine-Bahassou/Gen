## Building a Currency Converter App with Node.js

### Project Overview

In this guide, we'll build a simple command-line tool using Node.js to convert currencies. It will take a user-defined amount and convert it from one currency to another based on real-time exchange rates.

### Setting Up the Development Environment

1. **Install Node.js:** Visit the Node.js website and download the latest LTS (Long-Term Support) version for your operating system.
2. **Install a Code Editor:** Choose a code editor such as Visual Studio Code, Atom, or Sublime Text for writing your code.
3. **Create a New Repository:** Open your terminal or command prompt and create a new repository on GitHub or any other code hosting platform:
   ```
   git init
   git remote add origin <repository_url>
   ```

### Creating the Project Structure

1. **Create a New Directory:** Navigate to your preferred working directory and create a new directory for the project:
   ```
   mkdir currency-converter
   cd currency-converter
   ```
2. **Initialize npm:** Initialize a new npm project by running:
   ```
   npm init -y
   ```

### Writing the Necessary Code

1. **Create a `main.js` File:** This will be our main script file. Create it in the project directory and open it in your code editor.
2. **Import Necessary Modules:** Add the following lines to the top of the file:
   ```javascript
   const fetch = require('node-fetch');
   const readline = require('readline-sync');
   ```
3. **Define the Conversion Function:** We'll use the `fetch` module to retrieve real-time exchange rates and perform the conversion:
   ```javascript
   async function convertCurrency(from, to, amount) {
     const url = `https://api.exchangerate-api.com/v4/latest/${from}`;
     const response = await fetch(url);
     const data = await response.json();
     const rate = data.rates[to];
     return amount * rate;
   }
   ```
4. **Get User Input:** Use the `readline` module to prompt the user for input:
   ```javascript
   const from = readline.question('Enter the currency you want to convert from: ');
   const to = readline.question('Enter the currency you want to convert to: ');
   const amount = readline.question('Enter the amount you want to convert: ');
   ```
5. **Perform Conversion and Print Result:** Call the conversion function and print the result:
   ```javascript
   const convertedAmount = await convertCurrency(from, to, amount);
   console.log(`${amount} ${from} is equal to ${convertedAmount} ${to}.`);
   ```

### Running the Project

1. **Install Dependencies:** Run the following command to install the required dependencies:
   ```
   npm install
   ```
2. **Execute the Script:** Run the main script file using:
   ```
   node main.js
   ```

### Testing the Application

1. **Manual Testing:** Input different currencies and amounts to test the conversion accuracy.
2. **Unit Testing (Optional):** You can create unit tests to verify the conversion function's behavior.

### Adding Code to Repository and Pushing to Remote

1. **Add and Commit Changes:** Add the project files to the staging area and commit the changes:
   ```
   git add .
   git commit -m "Initial commit"
   ```
2. **Push to Remote:** Push the changes to your remote repository:
   ```
   git push origin main
   ```