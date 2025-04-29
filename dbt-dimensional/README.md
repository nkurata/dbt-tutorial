# dbt dimensional modeling Tutorial Repository

This repository contains my work as I follow a dbt (data build tool) tutorial, specifically focused on implementing a Kimball dimensional model.

## Tutorial Focus

The primary goal of this repository is to:

* Learn dbt fundamentals.
* Apply dbt to build a dimensional model following Kimball best practices.
* Use DuckDB as the local database for development.

## Project Structure

The repository is organized as a dbt project, with the following structure:

dbt-dimensional/
├── models/          # Contains dbt SQL models (transformations)
├── seeds/           # Contains CSV files for initial data loading
├── tests/           # Contains data quality tests
├── macros/          # (Optional) Reusable SQL code
├── dbt_project.yml  # dbt project configuration file
├── profiles.yml     # dbt connection profiles (local setup)
└── README.md        # Project documentation (this file)

## Getting Started

### Prerequisites

* **dbt Core:** Install dbt Core.  See the dbt documentation for installation instructions: [https://docs.getdbt.com/docs/core/installation-overview](https://docs.getdbt.com/docs/core/installation-overview)
* **dbt-duckdb adapter:** Install the dbt adapter for DuckDB: `pip install dbt-duckdb`
* **DuckDB:** While dbt-duckdb will handle creating the database, you might want to install the DuckDB CLI if you want to query the data directly.  You can install it via brew: `brew install duckdb` or download from the DuckDB website.

### Setup Instructions

1.  **Clone this repository:**
    ```bash
    git clone <your_repository_url>
    cd <your_repository_name>
    ```

2.  **Configure `profiles.yml`:**
    * dbt uses a `profiles.yml` file to manage database connections.  This file is usually located in your home directory at `~/.dbt/profiles.yml`.  If it doesn't exist, create it.
    * Add a profile for DuckDB.  A minimal `profiles.yml` might look like this:

        ```yaml
        your_project_name:  # Replace with your project name (e.g., adventureworks)
          target: dev
          outputs:
            dev:
              type: duckdb
              path: target/adventureworks.duckdb  # Path to your DuckDB database file (relative to the project)
        ```
        * Replace `your_project_name` with the name you've given the project in your `dbt_project.yml`
        * The `path` specifies where the DuckDB database file will be created.  The `target` directory is commonly used.

3.  **Install Dependencies (if any):**
    * If your dbt project has any package dependencies (defined in `packages.yml`), install them:
        ```bash
        dbt deps
        ```

## Running dbt

### Basic Commands

* **Seed Data:** Load initial data from CSV files (located in the `seeds` directory) into your DuckDB database:
    ```bash
    dbt seed --target duckdb
    ```
    * The `--target duckdb` flag ensures that dbt uses the DuckDB profile you configured.

* **Run Models:** Execute the SQL transformations defined in your dbt models (located in the `models` directory):
    ```bash
    dbt run --target duckdb
    ```

* **Test Data:** Run data quality tests defined in the `tests` directory:
    ```bash
    dbt test --target duckdb
    ```

* **Generate Documentation:** Create a documentation website for your dbt project:
    ```bash
    dbt docs generate --target duckdb
    ```

* **Serve Documentation:** Serve the documentation website locally:
    ```bash
    dbt docs serve --target duckdb
    ```

### Notes

* All dbt commands should be run from the root directory of your dbt project.
* The `--target duckdb` flag is crucial to ensure dbt uses your DuckDB configuration.

## Connecting to DuckDB Directly

To query the data directly using the DuckDB CLI:

1.  Open your terminal.
2.  Navigate to your dbt project directory.
3.  Connect to the DuckDB database file:
    ```bash
    duckdb target/adventureworks.duckdb
    ```
4.  Run SQL queries:
    ```sql
    SELECT * FROM <schema_name>.<table_name> LIMIT 10;
    ```
    * Replace `<schema_name>` (e.g., `sales`, `person`) and `<table_name>` (e.g., `salesorderheader`, `person`) with the actual schema and table names.
    * Use `.tables` to see a list of tables and schemas.
    * Use `.quit` or `.exit` to exit the DuckDB CLI.

##  Important Considerations for this Tutorial

* **Local Development:** This project is set up for local development using DuckDB.
* **Profiles:** The `profiles.yml` file is crucial for configuring the connection to your local DuckDB database.  Make sure the path is correct.
* **dbt Version:** This project was developed with dbt version 1.10.0.  It is recommended to use a compatible version. You can check your dbt version with `dbt --version`
* **Data Loading:** The `dbt seed` command is used to load data from CSV files into DuckDB.  Ensure that the CSV files in the `seeds` directory are in the correct location.

##  Next Steps

As I progress through the tutorial, I will:

* Add more detailed documentation.
* Include the SQL code for the dbt models.
* Document any challenges or interesting findings.
* Refactor for best practices

