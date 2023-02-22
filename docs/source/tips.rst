Tips & Tricks
=====
For the impatient:

Copy our current bash resource files into your home directory:

.. code-block:: console

    cp /projects/mjolnir1/apps/dotfiles/.bashrc ~/
    cp /projects/mjolnir1/apps/dotfiles/.bash_profile ~/

Zsh users should use this instead:

.. code-block:: console

    cp /projects/mjolnir1/apps/dotfiles/.zshrc ~/

For advanced users:

Add the following to your bash/tcsh/zsh resource files:

.. code-block:: console

    PATH=/projects/mjolnir1/apps/bin:~/bin:$PATH:/opt/software/miniconda/4.10.4/bin

Our default conda installation directory is ``/projects/mjolnir1/apps/conda`` and, by default, most bioinformatics tools are softlinked into ``/projects/mjolnir1/apps/bin``.

If you don't have specific needs concerning Python environments, our default ``py39`` environment covers most and is initiated in ``/projects/mjolnir1/apps/dotfiles/.bashrc``:

.. code-block:: console

    conda activate py39

Discord server
=====
Join our Discord server to get help from other users and search past messages.

The address for the discord server has been sent in your welcome email. 

When you join the Mjolnir Discord channel, it is important that you change your nickname to "Full name - KU-ID" and upload a photo of yourself. Users with no real name and KU-ID will be removed.
