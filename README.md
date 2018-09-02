# Production

    # clone repo
    git clone https://github.com/manyahin/mydiary.git
    cd mydiary
    
    # set password
    echo 'DIARY_PASSWORD=123456' > .docker-env

    # build
    docker-compose build

    # start production
    npm run prod

# Backup

    /backup/run.sh

Will make tar arhchive in backup folder and will upload it to Dropbox. Run /backup/dropbox_uploader.sh before to setup Dropbox token.

Restore by next command:

    tar -zxvf $FILE.tar.gz
    docker run --rm --network mydiary_default -v "$(pwd)/mongo_db":/backup \
      mongo:3.4 bash -c 'mongorestore /backup --host db:27017'