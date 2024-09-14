# Workout Engine

**Workout Engine** is a lightweight, flexible, and high-performance workout recommendation engine, designed for use in fitness applications. The engine takes user data, workout history, preferences, and configurations, and generates personalized workout recommendations. It also tracks user progress over time, using a strength model to help optimize workouts for individual users. The engine supports a wide range of exercise types, including resistance training, cardio, yoga, and calisthenics, and allows developers to customize the exercise database or integrate their own.

> [!WARNING]  
> This project is in the very early stages of development. Expect frequent changes and incomplete features. Contributions and feedback are welcome!

## Features

- **Personalized Workout Recommendations**: Generates customized workout plans based on user goals, preferences, and available equipment.
- **Exercise Database**: Comes with a comprehensive database of exercises, supporting a wide range of workout types such as resistance training, cardio, yoga, and calisthenics. The database can be extended or replaced by developers.
- **Strength Model**: Tracks user progress and estimates current strength based on historical data. The strength model adapts to the user’s workout history and provides insights into their fitness level.
- **Workout Modifiers**: Handles advanced workout modifiers like added or removed weights, incline/decline settings, band assistance or resistance, and variations of exercises.
- **Multi-Language Support**: Accessible through JavaScript (via npm) with bindings available for other languages like Python.
- **Extensible and Customizable**: Developers can easily add custom exercises, modify the default database, or integrate custom workout logic.

## Getting Started

### Prerequisites

- **Node.js** installed on your system.

### Installation

Install the **Workout Engine** package from npm:

```bash
npm install workout-engine
```
### Usage

Below are common usage examples showing how to initialize the engine, set user preferences, add workout data, and get recommendations.

1. Initialize the Engine

You can start by creating an instance of the engine and configuring it with user preferences:

```js
const WorkoutEngine = require('workout-engine');

const engine = new WorkoutEngine();
engine.setUserPreferences({
    goal: 'strength',
    equipment: ['barbell', 'dumbbells'],
    workout_time: 60  // in minutes
});
```

2. Adding Workout Data

Track workout sessions by adding them to the engine’s historical data:

```js
engine.addWorkoutData({
    exercise: 'Bench Press',
    sets: 4,
    reps: 8,
    weight: 80,  // weight in kilograms
    date: '2024-09-12'
});

```
3. Get a Workout Recommendation

The engine will generate a workout plan based on the user’s historical data, preferences, and strength model:

```js
const recommendation = engine.getWorkoutRecommendation();
console.log('Recommended workout:', recommendation);
```

4. Retrieve Strength Model

You can retrieve the current estimate of the user’s strength, which is calculated from their workout history:

```js
const strengthModel = engine.getStrengthModel();
console.log('Strength Model:', strengthModel);
```

### Exercise Data

By default, the engine includes a comprehensive exercise database, which you can customize. Each exercise includes fields such as:

Name (e.g., "Push-up")

Category (e.g., "strength", "cardio")

Muscle groups targeted

Difficulty rating

Equipment needed

Default sets and reps or duration


You can extend the database by providing a custom JSON file or through API calls:

```js
engine.addCustomExercises([
    {
        name: 'Pistol Squat',
        category: 'strength',
        muscle_groups: ['legs'],
        difficulty: 5,
        equipment: 'none',
        default_sets: 3,
        default_reps: 8
    }
]);
```

### Supported Workout Modifiers

The engine supports a range of workout variations, including:

Added/Removed Weight: Track exercises with extra or reduced resistance.

Incline/Decline: Adjust the difficulty by specifying an incline or decline.

Band Resistance/Assistance: Use resistance bands for added difficulty or assistance.

Tempo: Specify a tempo for exercises where it matters (e.g., strength training).


### Configuration

User preferences can be configured through simple API calls:

```js
engine.setUserPreferences({
    goal: 'endurance',
    equipment: ['treadmill'],
    workout_time: 30,
    incline_decline: 10,  // Set default incline for exercises like running
    weight: null,  // Default no weight added for most exercises
    bands: 'resistance',  // Default resistance band usage
});
```

### Custom Exercise Database

The engine includes a default exercise database but allows full customization:

1. Override the default database:

```js
engine.loadExerciseDatabase('./custom_exercises.json');

```

2. Add exercises dynamically:

```js
engine.addCustomExercise({
    name: 'Box Jump',
    category: 'calisthenics',
    muscle_groups: ['legs', 'core'],
    difficulty: 3,
    equipment: 'box',
    default_sets: 4,
    default_reps: 10
});
```



### Example Use Case

Here’s an example of how the Workout Engine might be used in a real-world scenario:

```js
const WorkoutEngine = require('workout-engine');

// Initialize the engine with user preferences
const engine = new WorkoutEngine();
engine.setUserPreferences({
    goal: 'weight_loss',
    equipment: ['kettlebell', 'resistance_band'],
    workout_time: 45
});

// Add some historical workout data
engine.addWorkoutData({
    exercise: 'Kettlebell Swing',
    sets: 5,
    reps: 15,
    weight: 24,  // 24 kg kettlebell
    date: '2024-09-10'
});

// Get a workout recommendation based on the user’s data
const recommendation = engine.getWorkoutRecommendation();
console.log('Workout recommendation:', recommendation);

// Retrieve the user’s strength model
const strengthModel = engine.getStrengthModel();
console.log('Strength Model:', strengthModel);
```

### Contributing

We welcome contributions from the community! If you’d like to contribute:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Open a pull request with a detailed description of your changes.

For any issues, feature requests, or questions, please open an issue on GitHub.

License

This project is licensed under the MIT License. See the LICENSE file for more details.
