## Weather Forecast Application with React Native

### Introduction

This guide will provide step-by-step instructions on building a simple weather forecast mobile application using React Native. React Native is a framework that allows you to create native mobile applications using JavaScript and React.

### Setup

**1. Create a Repository**

* Create a new repository on GitHub or any other version control platform.
* Clone the repository to your local machine.

**2. Set up the Development Environment**

* Install Node.js and npm (Node Package Manager).
* Install React Native CLI: `npm install -g react-native-cli`

### Project Structure

**3. Create a New React Native Project**

* Navigate to the cloned repository directory.
* Initialize a new React Native project: `npx react-native init WeatherApp`
* Navigate to the newly created project directory: `cd WeatherApp`

### Writing the Code

**4. Install Dependencies**

* Install the necessary dependencies: `npm install axios`

**5. Create the Main Screen**

* Create a file `App.js` in the `src` directory.
* Import `axios` and `useState` from `react`.
* Define the `App` component:

```javascript
import axios from "axios";
import { useState } from "react";

export default function App() {
  const [weatherData, setWeatherData] = useState(null);
  const [location, setLocation] = useState("");

  const fetchWeather = () => {
    axios
      .get(`https://api.openweathermap.org/data/2.5/weather?q=${location}&appid=YOUR_API_KEY`)
      .then((res) => setWeatherData(res.data))
      .catch((err) => console.error(err));
  };

  return (
    <View>
      <TextInput onChangeText={setLocation} value={location} />
      <Button title="Get Weather" onPress={fetchWeather} />
      {weatherData && <Text>{JSON.stringify(weatherData)}</Text>}
    </View>
  );
}
```

**6. Replace `YOUR_API_KEY`**

* Obtain an API key from OpenWeatherMap and replace `YOUR_API_KEY` in the `fetchWeather` function.

### Running the Project

**7. Run the Project**

* Start the Metro bundler: `npx react-native start`
* Open the project in an emulator or simulator.
* Scan the QR code to connect your device.

### Testing the Application

**8. Test the Application**

* Enter a location in the input field.
* Click the "Get Weather" button.
* The weather data should be displayed on the screen.

### Adding Code to Repository and Pushing to Remote

**9. Add Code to Repository**

* Stage the changes: `git add .`
* Commit the changes: `git commit -m "feat: initial weather app"`

**10. Push to Remote**

* Push the changes to the remote repository: `git push origin main`