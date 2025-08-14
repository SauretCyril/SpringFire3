# Forest Fire Simulation Application

## Overview

This application simulates forest fires using a backend built with Spring Boot and a frontend built with React. The backend handles the simulation logic and provides REST endpoints, while the frontend displays the simulation grid and allows user interaction.

## Application Installation

### Prerequisites

- Java 11 or higher
- Node.js and npm
- Maven

### Steps

1. Clone the repository:
   ```sh
   git clone https://github.com/SauretCyril/SpringFire3.git
   cd myForestSpringFire
   ```
2. Build backend
   - Navigate to the backend directory: root of project
   - Build the backend using Maven:
    ```sh
     mvn clean install
    ```
    This command will:
    - Clean the project (delete the target directory)
    - Compile the source code
    - Run tests
    - Package the application into a JAR file
    - Install the package into your local Maven repository

    Troubleshooting:
    - If you encounter Java version issues, ensure that JAVA_HOME points to Java 11+
    - For dependency issues, try `mvn dependency:resolve` to diagnose them
    - Use `mvn -X clean install` for detailed debug information
3.Build frontend
   - Navigate to the frontend directory: cd myForestSpringFire/my-app
   - Install dependencies:
     ```sh
     cd my-app
     npm install
     ```

## Troubleshooting

### Maven Command Not Found Error

Si vous rencontrez l'erreur: `mvn : Le terme «mvn» n'est pas reconnu comme nom d'applet de commande...`

#### Solution 1: Installer Maven
1. Téléchargez Maven depuis [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi)
   - Version recommandée: Maven 3.8.8 ou 3.9.6 pour Java 11+
   - Téléchargez le fichier "Binary zip archive" (apache-maven-3.9.6-bin.zip)
2. Extrayez l'archive dans un dossier de votre choix (ex: `C:\Program Files\Apache\maven`)
3. Ajoutez Maven au PATH système:
   - Ouvrez les Paramètres système > Variables d'environnement
   - Modifiez la variable PATH et ajoutez le chemin du dossier bin de Maven (ex: `C:\Program Files\Apache\maven\bin`)
   - Redémarrez votre terminal
 
#### Solution 2: Utiliser le Maven Wrapper
Si le projet contient déjà le Maven Wrapper, utilisez:
```sh
./mvnw clean install  # Pour Linux/macOS
# ou
mvnw clean install    # Pour Windows sans le ./
```

#### Solution 3: Utiliser le chemin complet
```sh
"C:\chemin\vers\maven\bin\mvn" clean install
```

#### Vérification
Après installation, vérifiez avec:
```sh
mvn -v
```

### Java Environment Variable Issues

Si vous rencontrez l'erreur: `The JAVA_HOME environment variable is not defined correctly`, même si vous pensez que JAVA_HOME est défini:

#### Solution: Vérification et correction de JAVA_HOME

1. **Vérifiez la valeur actuelle de JAVA_HOME**:
   ```sh
   echo %JAVA_HOME%  # Windows cmd
   $env:JAVA_HOME    # PowerShell
   ```

2. **Assurez-vous que JAVA_HOME pointe vers le répertoire d'installation de JDK** (pas jusqu'au dossier bin):
   - Format correct: `C:\Program Files\Java\jdk-11.0.12` 
   - Format incorrect: `C:\Program Files\Java\jdk-11.0.12\bin`

3. **Redéfinissez JAVA_HOME**:
   - Ouvrez Paramètres système > Variables d'environnement
   - Si JAVA_HOME existe, modifiez sa valeur; sinon, créez-la
   - Utilisez le chemin complet vers votre installation JDK
   
4. **Assurez-vous que %JAVA_HOME%\bin est dans votre PATH**:
   - Vérifiez que la variable PATH contient `%JAVA_HOME%\bin` (Windows)
   
5. **Vérifiez l'installation**:
   ```sh
   java -version
   javac -version
   ```
   Version ok : 
   -java 11 
   -spring boot 2.7.14
6. **Redémarrez votre terminal** après toute modification des variables d'environnement.

**Note**: Pour un même terminal déjà ouvert, les modifications des variables d'environnement ne sont pas prises en compte automatiquement. Vous devez fermer et rouvrir le terminal.

## Running the Application in local mode

1.be careful, you must create a file with json format named "config.json" with is configuration file of forest simulation fire 
you have tu put it in the 'projet root'\src\main\resources" directory

2.the file format must be :
{
    "height": 15,
    "width": 15,
    "probability": 0.8,
    "initialPositions": [
        [0, 0],
        [1, 1]
    ]
}

### Backend

1. Navigate to the project root directory.
2. Use the Maven Wrapper to start the backend:
   ```sh
   ./mvnw spring-boot:run
   ```
remark  : Once Swagger is configured, you can access the Swagger UI by opening the following URL in your browser:
   ```sh
   http://localhost:8080/swagger-ui.html
   ```

3. Navigate to the frontend directory
    ```sh
    cd my-app
    npm start
    ```

## Architecture

### Backend (Spring Boot)

- **Main Files:**
  - `DemoApplication.java`: Entry point of the Spring Boot application.
  - `SimulationController.java`: REST controller for handling simulation endpoints.
  - `ForestFireSimulation.java`: Class for the forest fire simulation logic.
  - `SimulationConfig.java`: Configuration class for the simulation.
  - `SwaggerConfig.java`: Configuration for Swagger/OpenAPI.

- **Configuration:**
  - `application.properties`: Configuration for the Spring Boot application.
  - `config.json`: Configuration file for the simulation.

- **Tests:**
  - `DemoApplicationTests.java`: Test class to verify the Spring context loading.

### Frontend (React)

- **Main Files:**
  - `App.tsx`: Main component of the React application.
  - `index.tsx`: Entry point of the React application.
  - `App.css`: CSS styles for the application.

- **Configuration:**
  - `package.json`: Dependencies and scripts for the React project.
  - `tsconfig.json`: TypeScript configuration for the React project.

- **Public:**
  - `index.html`: Main HTML file for the React frontend.
  - `manifest.json`: Web application manifest file.

## Features

### Backend

- **REST Endpoints:**
  - `GET /api/simulation/init`: Initializes the forest fire simulation.
  - `POST /api/simulation/step`: Advances the simulation by one step.

- **Simulation Logic:**
  - The `ForestFireSimulation` class handles the logic for simulating forest fires.

### Frontend

- **Grid Display:**
  - The `App.tsx` component displays the simulation grid and provides buttons for controlling the simulation ("Step" and "Reset").

- **API Calls:**
  - Uses axios to communicate with the Spring Boot backend.

## Dependencies

### Backend

- Spring Boot (Web, Test)
- H2 Database
- Jackson (for JSON serialization/deserialization)
- Springdoc OpenAPI (Swagger)

### Frontend

- React
- Axios (for API calls)
- TypeScript


# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

## GitHub Repository Information

### Comment identifier le nom du projet GitHub

Il existe une différence entre le nom du dépôt GitHub et le nom du dossier local après clonage:

1. **Le nom du dépôt GitHub**: "SpringFire3"
   - Visible dans l'URL: https://github.com/SauretCyril/SpringFire3.git
   - C'est le nom officiel du projet sur GitHub

2. **Le dossier local après clonage**: "myForestSpringFire" 
   - C'est le dossier dans lequel vous travaillez localement

Pour vérifier ces informations:

- **Depuis votre clone local**:
  ```sh
  git remote -v
  ```
  Cette commande affichera l'URL du dépôt distant, confirmant le nom GitHub.

- **Depuis GitHub**:
  - Visitez https://github.com/SauretCyril/SpringFire3
  - Le nom du projet est affiché en haut de la page

**Note**: Lors du clonage, vous pouvez spécifier un nom de dossier différent:
```sh
git clone https://github.com/SauretCyril/SpringFire3.git nom_de_dossier_personnalisé
```
