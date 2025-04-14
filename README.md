# Welcome to PowerDale

PowerDale is a small town with around 100 residents. Most houses have a smart meter installed that can save and send
information about how much power a house is using at a given point in time.

There are three major providers of energy in town that charge different amounts for the power they supply.

- _Dr Evil's Dark Energy_
- _The Green Eco_
- _Power for Everyone_

# Introducing JOI Energy

JOI Energy is a new start-up in the energy industry. Rather than selling energy they want to differentiate themselves
from the market by recording their customers' energy usage from their smart meters and recommending the best supplier to
meet their needs.

## Users

To trial the new JOI software 5 people from the JOI accounts team have agreed to test the service and share their energy
data.

| User    | Smart Meter ID  | Power Supplier        |
| ------- | --------------- | --------------------- |
| Sarah   | `smart-meter-0` | Dr Evil's Dark Energy |
| Peter   | `smart-meter-1` | The Green Eco         |
| Charlie | `smart-meter-2` | Dr Evil's Dark Energy |
| Andrea  | `smart-meter-3` | Power for Everyone    |
| Alex    | `smart-meter-4` | The Green Eco         |

These values are used in the code and in the following examples too.

## Requirements

The project requires [Java 17](https://adoptium.net/). If you have multiple JVMs on your machine, you might want to consider
using a tool such as [sdkman](https://sdkman.io/) or [mise](https://mise.jdx.dev/) to handle switching between versions.

The project uses Maven for dependency management and building.

## Useful Maven commands

### Build the project

Compiles the project, runs the tests and creates an executable JAR file:

```console
$ mvn clean package
Run the application using the executable JAR file:

console

$ java -jar target/developer-joyofenergy-java.jar
Run the tests
There are two types of tests:

Run unit tests only:

console

$ mvn test
Run functional tests (integration tests):

console

$ mvn verify -Pfunctional-test
Run all tests:

console

$ mvn verify
Run the application
Run the application which will be listening on port 8080:

console

$ mvn spring-boot:run
API
Below is a list of API endpoints with their respective input and output. The application needs to be
running for these endpoints to work.

Store Readings
Endpoint:

text

POST /readings/store
Example request body:

json

{
  "smartMeterId": "<smartMeterId>",
  "electricityReadings": [
    {
      "time": <epochSeconds>,
      "reading": <kWReading>
    }
  ]
}
Example using curl:

console

$ curl -X POST -H "Content-Type: application/json" "http://localhost:8080/readings/store" \
  -d '{"smartMeterId":"smart-meter-0","electricityReadings":[{"time":1606636800,"reading":0.0503},{"time":1606636860,"reading":0.0621}]}'
Get Stored Readings
Endpoint:

text

GET /readings/read/<smartMeterId>
Example:

console

$ curl "http://localhost:8080/readings/read/smart-meter-0"
Compare Price Plans
Endpoint:

text

GET /price-plans/compare-all/<smartMeterId>
Example:

console

$ curl "http://localhost:8080/price-plans/compare-all/smart-meter-0"
Get Recommended Price Plans
Endpoint:

text

GET /price-plans/recommend/<smartMeterId>[?limit=<limit>]
Example:

console

$ curl "http://localhost:8080/price-plans/recommend/smart-meter-0?limit=2"
Project Structure
Key files:

pom.xml - Maven project configuration

src/main/java - Application source code

src/test/java - Unit tests

src/functional-test/java - Functional tests

License
[Specify your license here]

Key changes made:
1. Changed Java requirement from 21 to 17
2. Replaced all Gradle commands with Maven equivalents
3. Updated build instructions to use Maven
4. Simplified the test running instructions
5. Removed Gradle-specific terminology
6. Kept all API documentation the same (as it's not build-system specific)
7. Added a project structure section mentioning key Maven files
8. Made the document more concise while preserving all essential information
