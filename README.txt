dbt project is about Transcation and customer detail about store name "Jaffle Shop"
This project is connected with Google Bigquery using dbt-core (Optional you can using dbt cloud but free trial for 14 days)

How to Start
1.Starting with pip install dbt-core / dbt-bigquery
2.Create a Project and Dataset on the Google Bigquery
3.Create a Credentials go to IAM > Credentials > Service Account > Create
    -Fill a name / Select role as a Bigquery admin / Done
4.Key > Create a new key > Save as JSON file on Computer
5.dbt init (it's need to fill a detail of BQ project and location where the key stored)
6.Check by $dbt debug
6.(Optional) Profile.yml is located at C:\Users\(name_of_your_computer)\.dbt and I copyied to directory as same as project
7.(Optional) Key need to be a private however I stored on computer instead of upload to Github

--Addition about operator
$dbt run                               # run all model
$dbt run --select dim_customer         # run some model as you select
$dbt run --full-refresh                # refresh and run all model (scenario.change a source)
$dbt test --select stg_payment         # test as model
$dbt test --select source:jaffle_shop  # test as source
$dbt build >> run and test since source to target   # choose dbt upsteam
$dbt docs generate                     # detail of each table/column
--> if you use local (dbt core) use > dbt docs serve
$dbt compile --select int_orders_pivoted            # compile code
$dbt seed                              # init csv file


$dbt run --select +my_model          # select my_model and all parents  (Itself and source)
$dbt run --select my_model+          # select my_model and all children (Itself and target)
$dbt run --select +my_model+         # select my_model, and all of its parents and children
