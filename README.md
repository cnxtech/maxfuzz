# Maxfuzz

## 🔍 Overview

Fuzzers like AFL and GoFuzz are *amazing* pieces of security engineering, but were clearly built to be run in an ad-hoc way. Some other attempts to help alleviate this problem exist (like afl-fuzz-docker and Cloudfuzzer), but here at Coinbase we needed something that would scale within AWS to suit our needs and not create lots of extra busywork for developers.

Taking some cues from [Google's ClusterFuzz](https://github.com/google/oss-fuzz/blob/master/docs/clusterfuzz.md), we built **Maxfuzz** - a fuzzing framework that abstracts the annoying and tedious bits of running a fuzzing campaign away and makes it easy to deploy fuzzers, collect results, and get back to the other important things you're doing.

## 🚀 Getting Started

This guide assumes you have Docker, docker-compose and make installed. For more on getting set up, please check out our [Development Environment Setup wiki page](). Most of the bootstrapping and deployment process is done through a [Makefile]() for simplicity and repeatability.

## 🐞 Find your first bug

First, build the base Maxfuzz Docker image: `make build`

Then spin up a local instance of Maxfuzz, running some [sample fuzzers](fuzzers/README.md): `make deploy-dev`

This launches a basic fuzzer that fuzzes some vulnerable C code, which can be found in `./fuzzers/vulnerable/`.

Upon deploying the fuzzer locally you should see some crashes appear fairly quickly in `./sync/afl-vulnerable/crashes/`.

As these crashes are uncovered by AFL, you should see corresponding logs from the Docker containers in the docker-compose view.

For more details on how to use Maxfuzz, please check out our [How to Use Maxfuzz wiki page]()

## 👷‍ Development

Contribution to this project is extremely welcome!

Please direct all Issues/Pull Requests to the [Bleeding Edge Repository]() - the [Coinbase Repository]() updates from there occasionally.

To get started, check out our wiki pages on:
- [Setting up your Development Environment]()
- [Architecture & Testing]()
- [Fuzzer Setup & Configuration]()
