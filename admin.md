## Installing Phishdetect Admin
Administration of phishdetect is performed through a python-flask application which can run your local machine, (for security reasons it's not advisable to run this on the same server which you run phishdetect-node.) To install and run the admin application follow the instructions here: https://github.com/phishdetect/phishdetect-admin

Install the dependences and run the `add-user.py` script in `phishdetect-node/scripts`

    <on server>
    pip3 install pymongo
    python3 phishdetect-node/scripts/add-user.py

Be sure to create an admin user and keep a note of the API key (ideally in your password manager.)

Now you can enter the node domain and the api key in the phishdetect admin tab. 
