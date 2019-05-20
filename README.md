## Créez votre Data Lake


### Utilisation

Commencez par installer les dépendances dans un environnement virtuel créé pour Python 3:

    cd ~/code
    virtualenv --python=python3 ./venv
    source ~/venv/bin/activate
    pip install fastavro hdfs

Clonez ce dépôt :

    git clone https://github.com/chrioniep/creez-votre-data-lake
    cd creez-votre-data-lake

Téléchargez les données géographiques dans un répertoire local dédié :

    mkdir -p ~/code/data/paris/raw
    python ./paris.py ~/code/data/paris/raw

Copiez les données vers HDFS (nécessite d'avoir un cluster HDFS en marche) dans le répertoire `/data/paris/raw` puis sérialisez ces données : 

    python serialize.py /data/paris/raw /data/paris/master

Vous pouvez afficher le contenu d'un fichier sérialisé en particulier en exécutant :

    python deserialize.py /data/paris/master/2.250182,48.824215,2.251182,48.825215.avro

