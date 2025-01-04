## Building a Currency Converter App with Node.js

### Step 1: Create a Repository

- Create a new repository on GitHub or any other version control platform.
- Clone the repository to your local machine.

### Step 2: Set Up the Development Environment

- Install Node.js and npm (Node Package Manager) on your system.
- Open a terminal window and navigate to the project directory.

### Step 3: Create the Project Structure

- Create a `package.json` file using `npm init -y`.
- Create a `src` directory to hold the source code.
- Inside `src`, create an `index.js` file.

### Step 4: Write the Necessary Code

- In `index.js`, add the following code:

```js
const axios = require('axios');
const currency = require('currency-codes');

const convertCurrency = async (from, to, amount) => {
  // Get exchange rate from fixer.io
  const response = await axios.get(
    `http://data.fixer.io/api/latest?access_key=${process.env.FIXER_API_KEY}&base=${from}&symbols=${to}`
  );

  // Calculate converted amount
  const rate = response.data.rates[to];
  const convertedAmount = amount * rate;

  // Format the output
  const formattedAmount = currency.format(convertedAmount, { symbol: currency.code(to) });

  // Return the converted amount
  return formattedAmount;
};
```

### Step 5: Run the Project

- Create a `.env` file and add your FIXER_API_KEY.
- In the terminal, run `node src/index.js <from> <to> <amount>`.
- Example: `node src/index.js USD EUR 100`

### Step 6: Test the Application

- Test the application with different currencies and amounts.
- Verify that the conversion is accurate.

### Step 7: Add Code to Repository and Push to Remote

- Add the changes to your local repository using `git add .`.
- Commit the changes using `git commit -m "feat: implement currency converter"`.
- Push the changes to the remote repository using `git push origin main`.