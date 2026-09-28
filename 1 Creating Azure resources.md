**Phase1**

Phase 1 involves setting up the Azure infrastructure that will allow me to do the homelab.

Setting up a new resource group. To start of the homelab, I have to create a new Azure resource group and configure it's settings. For simplisity ,I didn't change any default values, just gave it a name and created it in a zone near me (South Africa North).

<img width="1365" height="647" alt="Screenshot 2026-09-26 194853" src="https://github.com/user-attachments/assets/b425a2dc-97e6-4578-b3be-6a405132882f" />
<img width="1365" height="647" alt="Screenshot 2026-09-26 195054" src="https://github.com/user-attachments/assets/3ca42a59-eb8e-4700-842f-c9a733c6f708" />
<img width="1365" height="645" alt="Screenshot 2026-09-26 195133" src="https://github.com/user-attachments/assets/4c19ace7-58d6-4cea-9962-dfc0165ccdae" />

The second resource i had to create was a virtual net (VNet), this is the network to which my resources will associate to to ensure smooth connectivity.


<img width="1365" height="644" alt="Screenshot 2026-09-26 195834" src="https://github.com/user-attachments/assets/9dd301d2-23fd-4a58-9cec-6e29ed352c4b" />
<img width="1365" height="645" alt="Screenshot 2026-09-26 195940" src="https://github.com/user-attachments/assets/44ed10c9-40b7-47bd-9b65-f2791627dbb1" />
<img width="1365" height="647" alt="Screenshot 2026-09-26 200012" src="https://github.com/user-attachments/assets/cb49ced8-c0bb-4c90-bcb5-456a8f23d13b" />


The last resource  i had to create was a Virtual Machine. I created VM1 and VM2 using similar configurations using Windows Server Datacenter 2022 and a B-series instance size. I then created a NSG rule to allow Port 3389 only for my IP Address (to ensure highest level of security and is the recommended way to do this). I then changed the VM setting to allow the VM to have a static IP Address that should i restart or shut down, the IP Address persists. VM2 was configuring using the same deployment as VM1.

<img width="1365" height="646" alt="Screenshot 2026-09-26 200028" src="https://github.com/user-attachments/assets/2fe81f8a-e830-4869-a403-2870f8a09d74" />
<img width="1365" height="648" alt="Screenshot 2026-09-26 201155" src="https://github.com/user-attachments/assets/747c254b-bbc0-4711-b33d-dc26cf30c137" />
<img width="1365" height="646" alt="Screenshot 2026-09-26 201801" src="https://github.com/user-attachments/assets/d30a20b9-bd1a-4726-a4af-c2b73201ecaa" />
<img width="1365" height="645" alt="Screenshot 2026-09-26 202117" src="https://github.com/user-attachments/assets/ce30116b-07f6-4fcc-83e9-38583764b7b0" />
<img width="1365" height="647" alt="Screenshot 2026-09-26 202747" src="https://github.com/user-attachments/assets/94969cdc-993a-4ef7-9ebb-50b48112881c" />


