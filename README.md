# Georgetown Domains Push (GitHub Action)

(GH Actions Marketplace description): Copies the `docs` subdirectory to a path on your Georgetown Domains server specified by the `GU_DOMAINS_PATH` secret.
    
This Action takes all files/folders within the `docs` subdirectory of your repository and, upon completion of each push to your repository, copies these files/folders (using SCP) to the directory on your Georgetown Domains server specified by the `GU_DOMAINS_PATH` secret variable.

Note that you should set `GU_DOMAINS_PATH` *last*, as you'll need to specify all of the following secrets in order for the SCP copy to work:

* `HOST`: Your Georgetown Domains URL. For example, mine is `jpj.georgetown.domains`
* `USERNAME`: Your Georgetown Domains username. Note that this is **not** your UID, or any other non-GU domains username. It is the specific username assigned to you when you registered for Georgetown Domains. For example, mine is `jpjgeorg`
* `PASSWORD`: Your GU Domains password
* `GU_DOMAINS_PATH`: Finally, once the previous variables have been set up, you can set this secret to tell the Action where exactly where you want it to copy the contents of the `docs` subfolder (within your repo). In my case, for example, I usually copy the `docs` folder contents directly over to `/home/jpjgeorg/public_html/<name of repo>` (so, if my repo is named `dsan5000`, I set this to `/home/jpjgeorg/public_html/dsan5000/`, so that when people go to `https://jpj.georgetown.domains/dsan5000/` they see the rendered contents of the `docs` folder in the repo). But you can set this to be whatever path on Georgetown Domains you'd like the files to be copied to.