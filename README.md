# dino ( A nice dinosaurio )

You need a GitHub account

- Log into Github

- Add a git repository ( ex:hello )

- Log into Singularity Hub ( https://singularity-hub.org ) as the github user
  
    In the Hub add a new collection ( with the repository )

- Clone the git project
  
      git clone
      
      git clone git@github.com:<USER>/hello.git

in the directory "hello" add a Singularity definition file as "Singularity"

Ex:

    Bootstrap:docker
    From:ubuntu:16.04
    
    %labels
    MAINTAINER juanca09
    SPECIES Dinosaur
    
      %environment
    RAWR_BASE=/code
    export RAWR_BASE
    
      %runscript
    echo "This gets run when you run the image!" 
    exec /bin/bash /code/dino.sh "$@"
    
    
    %post 
    echo "This section happens once after bootstrap to build the image."  
    mkdir -p /code  
    echo "echo \"RoooAAAARRRRR !!!!\"" >> /code/dino.sh
    chmod u+x /code/dino.sh  

- Commit and push the project

