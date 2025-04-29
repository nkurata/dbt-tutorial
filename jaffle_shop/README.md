# My dbt tutorial Project

This project was set up following the [dbt Core manual installation guide](https://docs.getdbt.com/guides/manual-install?step=1).

## Prerequisites

* Basic understanding of Terminal commands (e.g., `cd`, `ls`, `pwd`).
* Appropriate setup and data loaded in your data warehouse (e.g., BigQuery).
* GitHub account (if you intend to use version control).

## Setup

1.  **Install dbt Core:** Follow the installation instructions for your operating system as detailed in the guide.
2.  **Connect to your data warehouse:** Configure your `profiles.yml` file with the necessary connection details.

## Getting Started

1.  **Run the example models:** Execute `dbt run` to ensure your connection is working and dbt is configured correctly.
2.  **Build your own models:** Create SQL files in the `models` directory to define your data transformations.
3.  **Test your models:** Add tests in YAML files to validate the accuracy and integrity of your models.
4.  **Document your models:** Provide descriptions for your models in the YAML files to enhance project clarity.
5.  **Generate documentation:** Use `dbt docs generate` and `dbt docs serve` to create and view documentation for your project.

## Further Resources

* [dbt Core Documentation](https://docs.getdbt.com/): The official dbt documentation is a comprehensive resource for all things dbt.
* [dbt Learn](https://learn.getdbt.com/): A free learning resource to help you master dbt.
