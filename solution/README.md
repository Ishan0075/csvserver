1. docker run infracloudio/csvserver:latest
ERROR: error while reading the file ".csvserver/inputdata": open .csvserver/inputdata: no such file or directory

2. Reason we ahevto mounth this file in the form of volume which is performed in the next stage.

3. small bash script which will populate all the 
script: gencsv.sh
#!/bin/bash


file=/test/csvserver/inputfile

echo "$1, $2" > ${file}

echo "$3, $4" >> ${file}

echo "$5, $6" >> ${file}

echo "$7, $8" >> ${file}

echo "$9, ${10}" >> ${file}

echo "${11}, ${12}" >> ${file}

echo "${13}, ${14}" >> ${file}

EXECUTE THE SCRIPT
sudo ./gencsv.sh 2 12 3 34 4 55 6 77 7 87 9 87 8 99

4. input file is mounted at /csvserver/inputdata inside the container:  
docker run -d -v /test/csvserver/inputfile:/csvserver/inputdata infracloudio/csvserver:latest   

5. connected to the shell of the container:
sudo docker exec -it 624b259bb9e2 bash

docker stop 624b259bb9e2
docker rm 624b259bb9e2

6. 

a. docker run -d -v /test/csvserver/inputfile:/csvserver/inputdata infracloudio/csvserver:latest -p 9393:9300
application is accessbible locally at 9393 port after port forwarding: http://localhost:9393/

b. seting env variable in the container.
docker run -d -p 9393:9300 -v /test/csvserver/inputfile:/csvserver/inputdata -e "CSVSERVER_BORDER=orange" infracloudio/csvserver:latest




