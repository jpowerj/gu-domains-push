# Georgetown Domains Push (GitHub Action)

(GH Actions Marketplace description): Copies the `docs` subdirectory to a path on your Georgetown Domains server specified by the `GU_DOMAINS_PATH` secret.
    
This Action takes all files/folders within the `docs` subdirectory of your repository and, upon completion of each push to your repository, copies these files/folders (using SCP) to the directory on your Georgetown Domains server specified by the `GU_DOMAINS_PATH` secret variable.

Note that you should set `GU_DOMAINS_PATH` *last*, as you'll need to specify all of the following secrets in order for the SCP copy to work:

* `HOST`: Your Georgetown Domains URL. For example, mine is `jpj.georgetown.domains`
* `USERNAME`: Your Georgetown Domains username. Note that this is **not** your UID, or any other non-GU domains username. It is the specific username assigned to you when you registered for Georgetown Domains. For example, mine is `jpjgeorg`
* `PORT`: Since we're copying to Georgetown Domains using SCP, this should pretty much always be set to **22**. I wanted to include it as a variable, though, just in case something changes in the future.
* `SSH_PRIVATE_KEY`: This is probably the least intuitive part. You have to take the contents of the `id_rsa` file that was created when you first enabled SSH access to your Georgetown Domains server (through the [https://georgetown.domains/dashboard](https://georgetown.domains/dashboard) interface), and copy its contents **exactly** into the `SSH_PRIVATE_KEY` secret.
* `SSH_PRIVATE_KEY_PASSPHRASE`: For extra security, your Georgetown Domains SSH private key should also be protected by a passphrase, that it gave you the option to create when you first generated the SSH key using the [https://georgetown.domains/dashboard](https://georgetown.domains/dashboard) interface. Include that passphrase as a secret with this name.
* `GU_DOMAINS_PATH`: Finally, once the previous variables have been set up, you can set this secret to tell the Action where exactly where you want it to copy the contents of the `docs` subfolder (within your repo). In my case, for example, I usually copy the `docs` folder contents directly over to `/home/jpjgeorg/public_html/<name of repo>`. But you can set this to be whatever path on Georgetown Domains you'd like the files to be copied to.
