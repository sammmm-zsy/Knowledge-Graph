# Knowledge-Graph (win - python3.7 py2neo + neo4j)
I am willing to record my path of learning knowledge graph <3

## Before Neo4j
### Install JDK
I tried to install JDK 17 but I got an error which is `Neo4j Server shutdown initiated by request`, then I tried JDK-12, it worked.

Download link here: [Java Archive](https://www.oracle.com/java/technologies/downloads/archive/)

### Configure environment variables
- Properties -> Advanced system settings -> Environment variables -> New

  **Variable name:** `JAVA_HOME`

  **Variable value:** JDK install path, for example `E:\java\jdk-12`

- Path, enter `%JAVA_HOME%\bin`

- Check if the installation is successful: ctrl R -> cmd -> enter `java -version`

## Install Neo4j(mine is neo4j-community-4.2.19)
Download link here: [Neo4j download center](https://neo4j.com/download-center/#community)

[The Neo4j Operations Manual v5](The Neo4j Operations Manual v5)

### Configure environment variables
- Properties -> Advanced system settings -> Environment variables -> New

  **Variable name:** `NEO4J_HOME`

  **Variable value:** Neo4j name, for example `neo4j-community-4.2.19`

- Path, enter `%NEO4J_HOME%\bin`

- Check if the installation is successful: 
  Run powershell as an administrator, enter 
  ```
  cd E:\neo4j\neo4j-community-4.2.19\bin # your own neo4j path
  .\neo4j.bat console
  ```
  If you got a localhost return, copy that to your browser. Username and password for first login are both `neo4j`
  
  ## Install py2neo
  Use`pip install py2neo`
  
  ## In the very last, test if it works
  - enter those code in your jupyter notebook
  
  ```
  from py2neo import Graph, Node, Relationship

  # type your own username and password
  g = Graph('http://localhost:7474', auth = ('username', 'password'))

  a = Node("hero", name="Clint")  # Node(label, name)
  b = Node("hero", name="Natasha")
  ab = Relationship(a, "friend", b)
  g.create(ab)  # creat link and node
  ```
  
   - enter `match(n) return n;` code in neo4j.
   
   **Congratulations, you have obtained your first "knowledge graph" :D**
