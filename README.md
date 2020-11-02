# Genomics Workflows on AWS

[![Build Status](https://travis-ci.com/aws-samples/aws-genomics-workflows.svg?branch=master)](https://travis-ci.com/aws-samples/aws-genomics-workflows)

This repository is the source code for [Genomics Workflows on AWS](https://docs.opendata.aws/genomics-workflows).  It contains markdown documents that are used to build the site as well as source code (CloudFormation templates, scripts, etc) that can be used to deploy AWS infrastructure for running genomics workflows.

## Large-Scale Enhancements

### Building

Edit the template `nextflow-aio.template.yaml` for the desired number of availability zones.  The parameters defined here are passed to the template `https://aws-quickstart.s3.amazonaws.com/quickstart-aws-vpc/templates/aws-vpc.template` which is fetched during the installation.  This template can create a maximum of 4 availability zones; bear in mind that not all regions have 4 availability zones.  For the desired number of availability zones, edit:

* `Resources` - `VpcStack` - `Properties` - `Parameters` - `AvailabilityZones`
    * Add lines defining regions `c`, `d` as appropriate
* `Resources` - `VpcStack` - `Properties` - `Parameters` - `NumberOfAZs`
    * Define 2, 3, or 4 as appropriate
* `Resources` - `GenomicsWorkflowStack` - `Properties` - `Parameters` - `SubnetIds`
    * Add to this list `PrivateSubnet3AID`, `PrivateSubnet4AID` as appropriate

## Building the documentation

The documentation is built using mkdocs.

Install dependencies:

```bash
$ conda env create --file environment.yaml
```

This will create a `conda` environment called `mkdocs`

Build the docs:

```bash
$ source activate mkdocs
$ mkdocs build
```

## License Summary

This sample code is made available under a modified MIT license. See the LICENSE file.