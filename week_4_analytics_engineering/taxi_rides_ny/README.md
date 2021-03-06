Welcome to your new dbt project!

### How to run this project 
#### Prerequisites
We will build a project using dbt and a running data warehouse. 
By this stage of the course you should have already: 
- A running warehouse (BigQuery or postgres) 
- A set of running pipelines ingesting the project dataset (week 3 completed): [Taxi Rides NY dataset](dataset.md)

#### Setting up dbt for using BigQuery (Alternative A - preferred)
You will need to create a dbt cloud account using [this link](https://www.getdbt.com/signup/) and connect to your warehouse [following these instructions](https://docs.getdbt.com/docs/dbt-cloud/cloud-configuring-dbt-cloud/cloud-setting-up-bigquery-oauth). 

_Optional_: If you feel more comfortable developing locally you could use a local installation of dbt as well. You can follow the [official dbt documentation](https://docs.getdbt.com/dbt-cli/installation) or use a docker image from oficial [dbt repo](https://github.com/dbt-labs/dbt/). You will need to install the latest version (1.0) with the BigQuery adapter (dbt-bigquery).
After local installation you will have to set up the connection to BQ in the `profiles.yml`, you can find the templates [here](https://docs.getdbt.com/reference/warehouse-profiles/bigquery-profile)


#### Setting up dbt for using Postgres locally (Alternative B)
As an alternative to the cloud, that require to have a cloud database, you will be able to run the project installing dbt locally.
You can follow the [official dbt documentation](https://docs.getdbt.com/dbt-cli/installation) or use a docker image from oficial [dbt repo](https://github.com/dbt-labs/dbt/). You will need to install the latest version (1.0) with the postgres adapter (dbt-postgres).
After local installation you will have to set up the connection to PG in the `profiles.yml`, you can find the templates [here](https://docs.getdbt.com/reference/warehouse-profiles/postgres-profile


### About the project
This project is based in [dbt starter project](https://github.com/dbt-labs/dbt-starter-project) (generated by running `dbt init`)
Try running the following commands:
- dbt run
- dbt test

A project includes the following files: 
- dbt_project.yml: file used to configure the dbt project. If you are using dbt locally, make sure the profile here matches the one setup during installation in ~/.dbt/profiles.yml
- *.yml files under folders models, data, macros: documentation files
- csv files in the data folder: these will be our sources, files described above
- Files inside folder models: The sql files contain the scripts to run our models, this will cover staging, core and a datamarts models. At the end, these models will follow this structure: 

![image](https://user-images.githubusercontent.com/4315804/148698374-b3163748-a2a2-4dc8-910e-207f19e08fbc.png)

#### Workflow
![image](https://user-images.githubusercontent.com/4315804/148699280-964c4e0b-e685-4c0f-a266-4f3e097156c9.png)

#### Execution
After having installed the required tools and cloning this repo, execute the following commnads: 

1. Change into the project's directory from the command line: `$ cd [..]/taxi_rides_ny`
2. Load the CSVs into the database. This materializes the CSVs as tables in your target schema: `$ dbt seed`
3. Run the models: `$ dbt run`
4. Test your data: `$ dbt test`
_Alternative: use `$ dbt build` to execute with one command the 3 steps above together_
5. Generate documentation for the project: `$ dbt docs generate`
6. View the documentation for the project, this step should open the documentation page on a webserver, but it can also be accessed from  http://localhost:8080 : `$ dbt docs serve`

### dbt resources:
- Learn more about dbt [in the docs](https://docs.getdbt.com/docs/introduction)
- Check out [Discourse](https://discourse.getdbt.com/) for commonly asked questions and answers
- Join the [chat](http://slack.getdbt.com/) on Slack for live discussions and support
- Find [dbt events](https://events.getdbt.com) near you
- Check out [the blog](https://blog.getdbt.com/) for the latest news on dbt's development and best practices
