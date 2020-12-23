# DAT164 - Create Data Flows Covering Both SAP and Non-SAP Data Sources Using SAP Data Intelligence

[![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/teched2020-DAT164)](https://api.reuse.software/info/github.com/SAP-samples/teched2020-DAT164)

## Description

This repository contains the material for the SAP TechEd 2020 session <b>DAT164 - Create Data Flows Covering Both SAP and Non-SAP Data Sources Using SAP Data Intelligence</b>.

## Overview

This session introduces attendees to the capabilities of SAP Data Intelligence.
Focus is on the following features:

* SAP systems and sources (SAP Analytics Cloud, SAP ECC, SAP S/4 HANA, SAP HANA Cloud, SAP Cloud Applications) together with
* Non-SAP sources (AWS S3, Kafka, HDFS, Oracle) and
* Operationalize Code and Logic (Python, NodeJS, R, …) into a
* End-to-end Data Flow

## Demo Scenario

* Imagine you are the owner of an online shop that is offering a broad assortment. Apart from storing related product master data in your SAP HANA Cloud system you do also collect given product reviews that are stored in a Cloud Object Store (AWS S3 in this case). 
* In order to get a better understanding of the assessment of your products given by your customers you think of combining both the structured world reflected by SAP HANA Cloud and the rather semi-structured world represented by AWS S3 (this is covered in [Exercise 1](exercises/ex1/)). In order to create powerful ad-hoc visualizations you do also push the generated result set to SAP Analytics Cloud (see [Exercise 2](exercises/ex2/))
* The overall idea is not only to combine the datasets originating from both worlds but also to leverage the collected information by making use of OpenSource Machine Learning frameworks as the Natural Language Processing (NLP) library in Python. Precisely, it is the objective to apply a Sentiment Analysis on top of the dataset that is generated via joining the product master data stored in SAP HANA Cloud as well as the product reviews persisted in AWS S3 (this is part of [Exercise 3](exercises/ex3/)).
* Last but not least, you want to make use of advanced Business Intelligence methodologies to create powerful visualizations going forward. For this matter, you will benefit from the possibility to immediately push the derived result sets to SAP Analytics Cloud (see [Exercise 4](exercises/ex4/)).

## Requirements

No SAP Data Intelligence knowledge is needed to follow this tutorial.

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
