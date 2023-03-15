VPN access and login
====

In order to connect to Mjolnir, a connection to the KU-IT VPN is required using **Cisco AnyConnect**. 

**There is no exception to this**. 

Due to special customization of the software, you can only use **Cisco AnyConnect** which have to be downloaded from https://vpn.ku.dk. Versions downloaded from other websites or used previously at other institutions will not work.

For any problems with KU VPN, please go to 
https://kunet.ku.dk/employee-guide/Pages/IT/Remote-access.aspx 
or contact KU-IT. We can not help you with problems related to VPN.

Login is only possible when you are connected to the KU-VPN using **Cisco AnyConnect**.
After you have successfully connected to the VPN, launch your favorite terminal application and type:

.. code-block:: console

   ssh <KU-ID>@mjolnirhead01fl.unicph.domain

Remember to replace ``<KU-ID>`` with your own KU userID.
Your password is the same password you have associated with your KU-ID.

We have one login node which is called **mjolnirhead01fl** (:doc:`hardware`). **No heavy computation** is allowed at this node, as this is the entrance to Mjolnir for every registered user we have. If the node goes down, nobody will be able to login.

If you are successfully connected to KU VPN using **Cisco AnyConnect**, but is otherwise unable to login to Mjolnir, please contact Bent.

SSH shortcut
=====

If you connect to Mjolnir often, you may wish to create an SSH shortcut to save you time typing. To do this, you'll have to edit your SSH config file on your local computer:

.. code-block:: console

   vi ~/.ssh/config
   
With the following lines:

.. code-block:: console

   host mj
      Hostname mjolnirhead01fl.unicph.domain
      User YOUR-KU-ID
      ServerAliveInterval 60
      
Once you've reloaded your bash session (or reopened your terminal program), you can now connect using the following shortcut:

.. code-block:: console

   ssh mj
