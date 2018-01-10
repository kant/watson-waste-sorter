[![Build Status](https://travis-ci.org/IBM/watson-waste-sorter.svg?branch=master)](https://travis-ci.org/IBM/watson-waste-sorter)
![IBM Cloud Deployments](https://metrics-tracker.mybluemix.net/stats/a9da622b1e6fbfdc883c6a1c0ca2e171/badge.svg)

# watson-waste-sorter
***Work in progress***

## Included components

* [Watson Visual Recognition](https://www.ibm.com/watson/developercloud/visual-recognition.html): Visual Recognition understands the contents of images - visual concepts tag the image, find human faces, approximate age and gender, and find similar images in a collection.

## Deploy the Server Application to IBM Cloud

[![Deploy to IBM Cloud](https://metrics-tracker.mybluemix.net/stats/a9da622b1e6fbfdc883c6a1c0ca2e171/button.svg)](https://console.ng.bluemix.net/devops/setup/deploy/?repository=https://github.com/IBM/watson-waste-sorter)

# Steps

First provision a Free tier [Visual Recognition](https://console.bluemix.net/catalog/services/visual-recognition) 
Service and name it `visual-recognition-wws`.

Then, push the application to Cloud Foundry
```
cf push
```

## Backend API usage

Do a POST request at `https://watson-waste-sorter.mybluemix.net/api/sort` with the image as the parameter. 
Return value should be in JSON.

Example in Bash:

Input: png/jpg/jpeg file
```
curl -X POST -F "images_file=@plastic_fork.jpg" "https://watson-waste-sorter.mybluemix.net/api/sort"
```

Output: 
```
{"status code": 200, "result": "landfill", "accuracy rate": 0.908}
```

## Privacy Notice

If using the Deploy to IBM Cloud button some metrics are tracked, the following information is sent to a [Deployment Tracker](https://github.com/IBM/metrics-collector-service) service on each deployment:

* Python package version
* Python repository URL
* Application Name (`application_name`)
* Application GUID (`application_id`)
* Application instance index number (`instance_index`)
* Space ID (`space_id`) or OS username
* Application Version (`application_version`)
* Application URIs (`application_uris`)
* Cloud Foundry API (`cf_api`)
* Labels of bound services
* Number of instances for each bound service and associated plan information
* Metadata in the repository.yaml file

This data is collected from the `setup.py` and `repository.yaml` file in the sample application and the `VCAP_APPLICATION` and `VCAP_SERVICES` environment variables in IBM Cloud and other Cloud Foundry platforms. This data is used by IBM to track metrics around deployments of sample applications to IBM Cloud to measure the usefulness of our examples, so that we can continuously improve the content we offer to you. Only deployments of sample applications that include code to ping the Deployment Tracker service will be tracked.

## Disabling Deployment Tracking

To disable tracking, simply remove ``metrics_tracker_client.track()`` from the ``run.py`` file in the top level directory.

# License

[Apache 2.0](LICENSE)