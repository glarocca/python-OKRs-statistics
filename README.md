# OKR-statistics

This repository contains python clients to produce statistics that can be
used by EGI Foundation team to identify trends and monitor progress following
the **Objectives and Key Results (OKRs)** goal-setting framework.

* **Cloud CPU/h** consumed by the production VOs of EGI
* **HTC CPU/h** consumed by the production VOs of EGI
* Num. of **'active'**, **'total'** and **'actual'** users of the production
  VOs registered in the [EGI Operations Portal](https://operations-portal.egi.eu/)
* Num. of Service Orders (SOs) received from the [EOSC MarketPlace](https://marketplace.eosc-portal.eu/)
* ...

The statistics generated by these python clients will be pushed in a Google
Worksheet using the [gspread](https://docs.gspread.org/en/v5.10.0/) APIs

## Pre-requisites

* `Python 3.10.12+` installed on your local computer
* Install pip3: `apt-get install -y python3-pip`
* Install gspread API: `sudo pip3 install gspread`
* Install venv: `sudo apt install -y python3-venv`

## Creating a Google Service Account

In order to read from and write data to Google Sheets in Python,
we will have to create a **Google Service Account**.

**Instructions** to create a Google Service Account are the following:

* Head over to [Google developer console](https://console.developers.google.com/) and click on **Create Project**
* Fill in the required fields and click on **Create**
* Click on **Enable API and Services**
* Search for Google Drive API and click on **Enable**
* Search for the Google Sheets API and click on **Enable**
* Click on **Create Credentials**
* Select **Google Drive API** as the API and Web server
* Name the service account, then grant it a **Project** role with **Editor** access
* Click on **Continue**
* The credentials will be created and downloaded as a JSON file
* Copy the JSON file to your code directory and rename it to `credentials.json`

## Configuring the environment

Use virtualenv to configure the working environment:

```shell
]$ virtualenv -p /usr/bin/python3.10 venv
created virtual environment CPython3.10.12.final.0-64 in 1748ms
[..]

]$ source venv/bin/activate
```

Install the library `gspread` with pip3:

```shell
]$ pip3 install gspread
[..]
```

## Avaliable clients

This GitHub repository includes clients to calculate:

* [The HTC and Cloud CPU/h of the VOs of the EGI Federation](pyOKR_VOs_CPUs_Accounting)
* [The number of users in the production VOs of the EGI Federation](pyOKR_VOs_Users_Accounting)
