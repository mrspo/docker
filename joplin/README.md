## Joplin
1. Deploy:
    ``` bash
    mkdir ~/docker/containers/joplin/data/postgres -p
    nano ~/docker/containers/joplin/compose.yaml
    [copy compose.yaml]
    nano ~/docker/containers/joplin/.env
    [copy .env]
    docker compose -f ~/docker/containers/joplin/compose.yaml up -d
    ```

2. Open a browser to the admin portal at ```http://[server IP]:22300``` with default creds ```admin@localhost```, ```admin``` - change this.

3. An email will be sent to confirm the account but will fail since there is no email server set up. Instead navigate to Admin > Emails and open the email 'Confirm your new Joplin Server account email', then click the confirm email link.

4. The server is now available for note-taking. Install the [Joplin app](https://joplinapp.org/help/install/) on PC, Mac, Android, iOS, and Linux. From the app, navigate to configuration > synchronisation and select synchronisation target ```Joplin Server```. Enter the server info and credentials and click ```Check Synchronisation Configuration``` to verify it works.

5. All notes are saved inside the database, figure out a good backup. If you want to save notes as documents, refer to the [documentation](https://hub.docker.com/r/joplin/server) for [adding a storage driver.](https://hub.docker.com/r/joplin/server#setup-storage)