Software Engineering Methods
name: A workflow for my Hello World App
on: push

jobs:
build:
name: Hello world action
runs-on: ubuntu-20.04
steps:
- name: Checkout
uses: actions/checkout@v2
- name: Set up JDK 11
uses: actions/setup-java@v2
with:
java-version: '11'
distribution: 'adopt'
- name: Compile with Maven
run: mvn compile
- name: Build Docker Image
run: docker build -t devopsimage .
- name: Run image
run: docker run --name devopscontainer -d devopsimage
- name: view logs
run: docker logs devopscontainer
- ![workflow](https://github.com/<UserName>/<RepositoryName>/actions/workflows/main.yml/badge.svg)