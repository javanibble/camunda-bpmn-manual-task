# Implement a BPMN Manual Task in Camunda
The article contains a step-by-step guide on how to implement a BPMN Manual Task in Camunda making use of a Spring Boot Application. A Manual Task is a Task that is not managed by any business process engine. It can be considered as an unmanaged Task, unmanaged in the sense of that the business process engine doesn’t track the start and completion of such a Task.

**Java Nibble Article:** [https://www.javanibble.com/implement-bpmn-manual-task-in-camunda/](https://www.javanibble.com/implement-bpmn-manual-task-in-camunda/)

**Pre-Requisites**
The following is required to run the Spring Boot example:
* [curl](https://www.javanibble.com/how-to-install-curl-on-macos-using-homebrew/)
* jq
* [maven](https://www.javanibble.com/how-to-install-maven-on-macos-using-homebrew/)

## BPMN Manual Task
A Manual Task defines a task that is external to the BPM engine. It is used to model work that is done by somebody who the engine does not need to know of and is there no known system or UI interface. For the engine, a manual task is handled as a pass-through activity, automatically continuing the process at the moment the process execution arrives at it.

Use Camunda Modeller to model the process. The process model is composed of four manual tasks:

![BPMN Manual Task](https://www.javanibble.com//assets/images/posts/bpmn-manual-task/camunda-bpmn-manual-task.png)

* Retrieve Coffee Order: Is a `Manual Task` linked to an Execution Listener with a Delegate Expressions value of `${executionlistener}`.
* Make Coffee: Is a `Manual Task` linked to an Execution Listener with a Delegate Expressions value of `${executionlistener}`.
* Pour Coffee in Cup: Is a `Manual Task` linked to an Execution Listener with a Delegate Expressions value of `${executionlistener}`.
* Deliver Coffee Order: Is a `Manual Task` linked to an Execution Listener with a Delegate Expressions value of `${executionlistener}`.


## Compile & Run The Example

### 1. Compile the application
Use the following command to compile the Spring Boot application making use of maven:

```shell
$ mvn clean install
```

### 2. Run the application
After you have successfully built the Camunda BPM Spring Boot application, the compiled artifact can be found in the
target directory. Use the following command to start the Camunda BPM Spring Boot Application.

```shell
$ maven spring-boot:run
```

### 3. Execute the example
After the application has started, run the following command in another terminal:

**Run the command: Start Process Instance**

The following command instantiates a new instance of the `order-coffee` process.

```shell
$ ./run_start_process.sh
```

The script performs the following commands:

```shell
curl --location --request POST 'http://localhost:8080/rest/process-definition/key/order-coffee/start' --header 'Content-Type: application/json'
``` 

The following is the output to the console after running the above command.

![Console](https://www.javanibble.com/assets/images/posts/bpmn-manual-task/console-camunda-bpmn-manual-task.png)

## Finally
Congratulations !!! You have successfully implemented a BPMN Manual Task in Camunda making use of a Spring Boot Application.