# DAT164 - Create Data Flows Covering Both SAP and Non-SAP Data Sources Using SAP Data Intelligence

## Description

This repository contains the material for the SAP TechEd 2020 session <b>DAT164 - Create Data Flows Covering Both SAP and Non-SAP Data Sources Using SAP Data Intelligence</b>.

## Overview

This session introduces attendees to the capabilities of SAP Data Intelligence.
Focus is on the following features:

* SAP systems and sources (SAP Analytics Cloud, SAP ECC, SAP S/4 HANA, SAP HANA Cloud, SAP Cloud Applications) together with
* Non-SAP sources (AWS S3, Kafka, HDFS, Oracle) and
* Operationalize Code and Logic (Python, NodeJS, R, …) into a
* End-to-end Data Flow

To quickly describe the use case, the underlying idea is to combine structured Product Master Data stored in SAP HANA Cloud and semi-structured Product Reviews that have been gathered in a Cloud Object Store (in this case, AWS S3 is utilized). This process is covered in [Exercise 1](exercises/ex1/). The goal of the subsequent [Exercise 2](exercises/ex2/) is to push the generated result set from [Exercise 1](exercises/ex1/) to SAP Analytics Cloud. This push is generating a dataset in SAP Analytics Cloud which can be used to apply methodologies from (advanced) analytics accordingly. In [Exercise 3](exercises/ex3/), we take into account Open Source Machine Learning Framework to apply a Sentiment Analysis on top of the enriched product dataset. This generates two more attributes in the enriched product dataset that measure the assessment of users that have give their feedback on the listed products. Last but not least, in [Exercise 4](exercises/ex4/), we push the once more enriched product dataset to SAP Analytics Cloud for getting the opportunity to further apply methodologies from (advanced) analytics accordingly.

## Requirements

The requirements to follow the exercises in this repository are:

* None

## Exercises

- [Getting Started](exercises/ex0/)
- [Exercise 1 - Combine Reviews and Master Data](exercises/ex1/)
- [Exercise 2 - Push Data to SAP Analytics Cloud](exercises/ex2/)
- [Exercise 3 - Extend Reviews with Sentiment Scores](exercises/ex3/)
- [Exercise 4 - Push Result Set including Sentiment Scores to SAP Analytics Cloud](exercises/ex4/)

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License
Copyright (c) 2020 SAP SE or an SAP affiliate company. All rights reserved. This file is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSES/Apache-2.0.txt) file.
