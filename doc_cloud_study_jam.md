### cloud study jam
Sat, 23-March 2019

output : share link url bash, 

facil : pak bambang dosen Akakom
1. [link](bit.ly/sj-ml1)
2. acces code : 1s-yogyakarta-1111

data engineering : extract, transform, load
data science : hubungannya dengan ML,AI

# 1. BigQuery: Qwik Start - Console
link belajar [link](https://google.qwiklabs.com/focuses/1145?parent=catalog)
google2823883_student@qwiklabs.net : sername
dS9q27Dk : pass
qwiklabs-gcp-57bc18715a8eaf0a : GCP project ID


* You can list the active account name with this command: gcloud auth list 
* You can list the project ID with this command: gcloud config list project

Query a public dataset :
input kan :
#standardSQL
SELECT
 weight_pounds, state, year, gestation_weeks
FROM
 `bigquery-public-data.samples.natality`
ORDER BY weight_pounds DESC LIMIT 10;


BUCKET
gsutil cp yob2014.txt gs://<your_bucket>


# 2. Bigtable: Qwik Start - Command Line
link belajar [link](https://google.qwiklabs.com/focuses/579?parent=catalog)
google2824147_student@qwiklabs.net
yZrn2tdyG
qwiklabs-gcp-9d67db3ff505b734


* echo project = [PROJECT_ID] > ~/.cbtrc
* echo project = qwiklabs-gcp-9d67db3ff505b734 > ~/.cbtrc
* echo instance = quickstart-instance >> ~/.cbtrc


jadi sebernya kita bisa akses learning nya, cuma gak bisa akses untuk google cloud platformnya
harus bayar, yang ini free...


# 2. Bigtable: Qwik Start - Hbase Shell
link belajar [link](https://google.qwiklabs.com/focuses/580?parent=catalog)
Downloading required files
1. git clone https://github.com/GoogleCloudPlatform/cloud-bigtable-examples.git
2. cd cloud-bigtable-examples/quickstart
3. ./quickstart.sh

Read and write data
Cloud Bigtable stores data in tables, which contain rows. Each row is identified by a row key.

Data in a row is organized into column families, or groups of columns. A column qualifier identifies a single column within a column family.

A cell is the intersection of a row and a column. Each cell can contain multiple versions of a value.

# 3. Cloud Natural Language API: Qwik Start
link belajar [link](https://google.qwiklabs.com/focuses/582?parent=catalog)
Cloud Natural Language API features
Syntax Analysis: Extract tokens and sentences, identify parts of speech (PoS) and create dependency parse trees for each sentence.

Entity Recognition: Identify entities and label by types such as person, organization, location, events, products and media.

Sentiment Analysis: Understand the overall sentiment expressed in a block of text.

Content Classification: Classify documents in predefined 700+ categories.

Multi-Language: Enables you to easily analyze text in multiple languages including English, Spanish, Japanese, Chinese (Simplified and Traditional), French, German, Italian, Korean and Portuguese.

Integrated REST API: Access via REST API. Text can be uploaded in the request or integrated with Google Cloud Storage.

In this lab you'll use the analyze-entities method to ask the Cloud Natural Language API to extract "entities" (e.g. people, places, and events) from a snippet of text.

terdapat 3 bagian :
1. analisis syntax 
2. semantik berhubungan dengan ontologi, keterkaitan dengan pemaknaan. setiap kata artinya apa.
3. pragmatik, sudah ada intensi tertentu. AI dulu itu gagal karen ingin membuat manusia. sudah mengikutsertakan konteks yang susah dipahami oleh mesin. ada cabang AI yang mampu mendekati proses ini, yaitu NLP.

chatbot => harus paham struktut, kemudian bahas artinya (semantik), dan terakhir konteksnya.
sentimen analisis => analisis terhadap kecenderungan tertentu.
content clasification => mengklasifikasikan dokumen
multi-language => analisis multi bahasa
integrated rest API => bisa dikerjakan dengan REST full API.

1. Create an API Key
    * export GOOGLE_CLOUD_PROJECT=$(gcloud config get-value core/project)
    * gcloud iam service-accounts create my-natlang-sa \
  --display-name "my natural language service account"
    * gcloud iam service-accounts keys create ~/key.json \
  --iam-account my-natlang-sa@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com
    * export GOOGLE_APPLICATION_CREDENTIALS="/home/USER/key.json"

2. make an entity procces
    Now you'll try out the Natural Language API's entity analysis with the following sentence:
Michelangelo Caravaggio, Italian painter, is known for 'The Calling of Saint Matthew'
    
   * gcloud ml language analyze-entities --content="Michelangelo Caravaggio, Italian painter, is known for 'The Calling of Saint Matthew'."

   output :
   `{
  "entities": [
    {
      "name": "Michelangelo Caravaggio",
      "type": "PERSON",
      "metadata": {
        "wikipedia_url": "http://en.wikipedia.org/wiki/Caravaggio",
        "mid": "/m/020bg"
      },
      "salience": 0.83047235,
      "mentions": [
        {
          "text": {
            "content": "Michelangelo Caravaggio",
            "beginOffset": 0
          },
          "type": "PROPER"
        },
        {
          "text": {
            "content": "painter",
            "beginOffset": 33
          },
          "type": "COMMON"
        }
      ]
    },
    {
      "name": "Italian",
      "type": "LOCATION",
      "metadata": {
        "mid": "/m/03rjj",
        "wikipedia_url": "http://en.wikipedia.org/wiki/Italy"
      },
      "salience": 0.13870546,
      "mentions": [
        {
          "text": {
            "content": "Italian",
            "beginOffset": 25
          },
          "type": "PROPER"
        }
      ]
    },
    {
      "name": "The Calling of Saint Matthew",
      "type": "EVENT",
      "metadata": {
        "mid": "/m/085_p7",
        "wikipedia_url": "http://en.wikipedia.org/wiki/The_Calling_of_St_Matthew_(Caravaggio)"
      },
      "salience": 0.030822212,
      "mentions": [
        {
          "text": {
            "content": "The Calling of Saint Matthew",
            "beginOffset": 69
          },
          "type": "PROPER"
        }
      ]
    }
  ],
  "language": "en"
}`

Read through your results. For each "entity" in the response, you'll see:

* The entity name and type, a person, location, event, etc.
* metadata, an associated Wikipedia URL if there is one
* salience, and the indices of where this entity appeared in the text. Salience is a number in the [0,1] range that refers to the centrality of the entity to the text as a whole.
* mentions, which is the same entity mentioned in different ways.
You've sent your first request to the Cloud Natural Language API.


# 3. Google Cloud Speech API: Qwik Start
API key : AIzaSyAGFamNSe-hlpNPXPs8MKY3daeCfV2U5To
* export API_KEY=AIzaSyAGFamNSe-hlpNPXPs8MKY3daeCfV2U5To
* touch request.json
* nano request.json
{
  "config": {
      "encoding":"FLAC",
      "sample_rate": 16000,
      "language_code": "en-US"
  },
  "audio": {
      "uri":"gs://cloud-samples-tests/speech/brooklyn.flac"
  }
}

* curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \
"https://speech.googleapis.com/v1beta1/speech:syncrecognize?key=${API_KEY}"

output :
{
  "results": [
    {
      "alternatives": [
        {
          "transcript": "how old is the Brooklyn Bridge",
          "confidence": 0.98267895
        }
      ]
    }
  ]
}

# 4. Dataproc: Qwik Start - Console
untuk clustering pekerjaan computer dalam mengelola data yang besar
salah satu yang dapat digunakan : apache spark dapat diakses menggunakan java, python, r


# 4. Dataproc: Qwik Start - Command Line
membuat cluster menggunakan command 
untuk membuat cluster :
* gcloud dataproc clusters create example-cluster

untuk submit job :
* gcloud dataproc jobs submit spark --cluster example-cluster \
  --class org.apache.spark.examples.SparkPi \
  --jars file:///usr/lib/spark/examples/jars/spark-examples.jar -- 1000

The command specifies:
* That you want to run a spark job on the example-cluster cluster
* The class containing the main method for the job's pi-calculating application
* The location of the jar file containing your job's code
* The parameters you want to pass to the job—in this case, the number of tasks, which is 1000

update cluster
* gcloud dataproc clusters update example-cluster --num-workers 4
* gcloud dataproc clusters update example-cluster --num-workers 2

# 5. Dataprep: Qwik Start


# 6. DataLab : Qwik Start
* datalab create my-datalab
isinya : ngoding python, dijalankan di mesinnya google, pakai VM.

# 7. Cloud ML Engine: Qwik Start
* menggunakan Tensorflow
* pip install --user --upgrade tensorflow
* git clone https://github.com/GoogleCloudPlatform/cloudml-samples.git
* cd cloudml-samples/census/estimator
* mkdir data
* gsutil -m cp gs://cloud-samples-data/ml-engine/census/data/* data/
* export TRAIN_DATA=$(pwd)/data/adult.data.csv
* export EVAL_DATA=$(pwd)/data/adult.test.csv
...

# 8. Data Studio: Qwik Start
Data Studio is a free, modern business intelligence product that lets you create dynamic, visually compelling reports and dashboards. With Data Studio, you can:

Easily connect to a variety of data sources.
Visualize your data through attractive, dynamic, and interactive reports and dashboards.
Share and collaborate with others, just as you can in Google Drive.
Data Studio automatically saves every change you make, so there's no need to click Save when editing a report.

In this lab you will create a report by pulling in a public dataset from BigQuery. You will then add a chart and style to your report, which will make your data elegant and easy to understand.


# 9. Google Genomics: Qwik Start
Uploads, processes, queries, and searches Genomics data in the cloud.
* export PROJECT=$(gcloud info --format='value(config.project)')
* export BUCKET=gs://${PROJECT}-genomics
* gsutil mb ${BUCKET}
* export BAM=gs://genomics-public-data/NA12878.chr20.sample.bam
* export BAI=${BUCKET}/NA12878.chr20.sample.bam.bai
* gcloud alpha genomics pipelines run \
    --regions us-east1 \
    --command-line 'samtools index ${BAM} ${BAI}' \
    --docker-image "gcr.io/genomics-tools/samtools" \
    --inputs BAM=${BAM} \
    --outputs BAI=${BAI}
output : Running [projects/qwiklabs-gcp-0b6abfaa71c7ea21/operations/8297629664328002768].
* gcloud alpha genomics operations wait 8297629664328002768

untuk mensimulasikan kemungkinan di masa mendatang


# 10. Dataflow: Qwik Start - Templates
Run the following command to create a dataset called taxirides:
* bq mk taxirides
* bq mk \
--time_partitioning_field timestamp \
--schema ride_id:string,point_idx:integer,latitude:float,longitude:float,\
timestamp:timestamp,meter_reading:float,meter_increment:float,ride_status:string,\
passenger_count:integer -t taxirides.realtime


Now that we have our table instantiated, let's create a bucket. Run the following commands to do so:
* export BUCKET_NAME=widya_bucket


# 10. Dataflow: Qwik Start - Python


# 11. Cloud Filestore: Qwik Start

















