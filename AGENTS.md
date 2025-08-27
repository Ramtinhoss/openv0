<general_rules>
Developers should adhere to the ESLint configurations present in the `webapps-starters/react/nextui/` and `webapps-starters/react/shadcn/` directories. These can be run using `npm run lint` within those specific webapp starter directories. Although a global linter or formatter is not explicitly defined, maintaining consistent code style is expected. New components and modules should follow the existing patterns found in the `server/build` and `server/library` directories.
</general_rules>
<repository_structure>
The repository is structured around three main components:
- **`npx/`**: This directory contains the `bin.js` entry point for the `npx openv0@latest` command, responsible for initial project setup and configuration.
- **`server/`**: This is the core backend. It includes:
    - `api.js`: The Express.js application handling API requests for component generation, listing, and sharing.
    - `db.js`: Manages SQLite database interactions, including building and populating the `openv0.sqlite` database with component and icon data.
    - `build/`: Modules responsible for parsing documentation and generating component and icon library assets (e.g., `dump.json`, `metadata.json`, `allowed_imports` for validation) into the `library/` directory.
    - `library/`: Stores the generated component and icon assets, including vector databases.
    - `modules/`: Contains modular pipelines, such as `multipass`, which is central to the generative UI component workflow.
    - `_test.js` files: These are individual scripts used for testing, validation, and demonstrating specific functionalities of the server components.
- **`webapps-starters/`**: This directory provides starter templates for different frontend frameworks (React, Svelte) and UI libraries (Flowbite, NextUI, Shadcn). Each sub-directory is a self-contained web application that can be used as a starting point.
The `server` and `webapps-starters` communicate via the API defined in `server/api.js`.
</repository_structure>
<dependencies_and_installation>
Dependencies are managed using `npm`. There are separate `package.json` files for the `npx` package, the `server` application, and each of the webapp starters.

**Quick Installation:**
The recommended way to get started is by running:
```sh
npx openv0@latest
```
This command will guide you through the setup, download `openv0`, and install necessary dependencies.

**Manual Installation:**
1.  Clone the repository.
2.  Navigate to the `server/` directory and run `npm install`.
3.  Unzip `server/library/icons/lucide/vectordb/index.zip` into the same folder.
4.  Configure your OpenAI API key by creating a `.env` file in the `server/` directory with `OPENAI_API_KEY=your_key_here`.
5.  Choose a web app starter from `webapps-starters/`, navigate into its directory (e.g., `webapps-starters/react/shadcn/`), and run `npm install`.
6.  Ensure the `WEBAPP_ROOT` variable in `server/.env` points to your chosen webapp folder path.

**Running the applications:**
-   Start the server: `cd server && node api.js`
-   Start the webapp: `cd webapp && npm run dev` (from the chosen webapp starter directory)
</dependencies_and_installation>
<testing_instructions>
While `server/package.json` contains a placeholder `"test": "echo \"Error: no test specified\" && exit 1"` script, testing in this repository is primarily handled through individual test scripts located in the `server/` directory, prefixed with `_test.` or ending with `.test.js`. Examples include `_test.build.js`, `_test.component_from_json.example.js`, `_test.db_build.js`, `_test.multipass.js`, and `_validate+postprocess.test.js`.

These scripts are designed to be run directly using Node.js (e.g., `node server/_test.build.js`) to validate specific functionalities, test different stages of the multipass pipeline, or demonstrate component generation. Developers should examine these existing test files to understand how to write and execute similar validation or example scripts for new features or modifications. There is no overarching test framework like Jest or Mocha configured to run all tests with a single command.
</testing_instructions>
<pull_request_formatting>
</pull_request_formatting>

