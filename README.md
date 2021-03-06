Neo Permissions
===============

Permission Resolution with Neo4j

Pre-Requisites
--------------

Clone and compile the batch-import project:

    git clone https://github.com/jexp/batch-import.git
    cd batch-import
    mvn clean compile assembly:single

See http://maxdemarzi.com/?s=batch for walk-through.

...or download [the jar file](https://dl.dropbox.com/u/57740873/batch-import-jar-with-dependencies.jar) from dropbox and copy it into generator directory.


Generator
---------

Sample graph data generator for this project.

Run:

    bundle install
    rake neo4j:install[enterprise,1.9.M05]
    rake neo4j:create (or rake neo4j:create_bigger)
    rake neo4j:load

Unmanaged
---------

Unmanaged Extension to find permissions including unit tests.

Run:

    mvn clean package
    cp target/unmanaged-extension-template-1.0.jar ../generator/neo4j/plugins/
    
Add to generator/neo4j/conf/neo4j-server.properties:

    org.neo4j.server.thirdparty_jaxrs_classes=org.neo4j.example.unmanagedextension=/example
    
Start Neo4j 

    rake neo4j:start

Performance
-----------

Gatling Stress Tool project to test the performance of unmanaged extension.

Use your favorite Java IDE to run Engine.scala and follow the prompts.
