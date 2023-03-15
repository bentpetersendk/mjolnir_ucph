Hardware
=====

Mjolnir consist of both CPU and GPU nodes, each with very different CPU/GPU and memory setups.
Please note the differences in architecture when you are booking your jobs as it will affect the efficiency of the running jobs. 
If you book more resources than you use, then you will limit your colleagues to compute as well. Its a balance that needs to be adjusted.

We have one login node which is called mjolnirhead01fl. No heavy computation is allowed at this node. Only rsync, sftp, editing data and moving data, or similar, is allowed. Mjolnirhead01fl is the entrance to Mjolnir for every registered user we have. If the node goes down, every user session will be terminated, every user will be logged out and nobody will be able to work.

.. raw:: html

       <iframe class="airtable-embed" src="https://airtable.com/embed/shrHPjHMhQNfumX7j?backgroundColor=green&viewControls=on" frameborder="0" onmousewheel="" width="100%" height="533" style="background: transparent; border: 1px solid #ccc;"></iframe>
       
