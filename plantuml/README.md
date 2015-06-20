Running PlantUML inside docker
===============================

`http://plantuml.sourceforge.net/command_line.html`


Example
========

```bash
    #Build the image ... see Dockerfile.template
    ./build

    #create two simple sequence diagrams
    echo -e "@startuml\nbob->amy:Hi\n@enduml" > example1.txt
    echo -e "@startuml\namy->bob:iH\n@enduml" > example2.txt

    #generate example1.png in local dir
    ./run ./example1.txt 

    #generate example2.png in other directory (/tmp/)
    ./run ./example2.txt /tmp/

    #generate *.png looking in local dir and putting files in (/tmp/)
    ./run . /tmp/

    #generate *.png looking in local dir and putting file in local dir
    ./run . .

```


