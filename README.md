# Ontap Select - Ansible playbook samples
----
This repository contains Ansible playbooks helping to automate the creation of an Ontap Select cluster, a Software-Defined Storage solution by NetApp.

Automate Ontap Select deployments could be useful to create an Ontap cluster environment for testing purpose (90 days evaluation license is provided with the image).

To use these playbooks you need to download the **NetApp Ansible roles repository**: <link>https://github.com/NetApp/ansible</link> and an Ontap Deploy OVA image from the NetApp site.
```
git clone https://github.com/NetApp/ansible.git NetApp-ansible-roles
```
Download this playbook repository:
```
git clone https://github.com/atosato/ansible-ontap-select.git ansible-ontap-select
```

**Tested with:**
 - Ansible: 2.8.5
 - Ontap Deploy OVA: ONTAPdeploy2.12.1.ova
----
## How to install Ontap Deploy

Place Ontap Deploy OVA image in the OntapSelectOVA folder:
`cp ONTAPdeployX.Y.Z.ova OntapSelectOVA/.`

Be sure that `na_ots_deploy/` role is installed in the repository. `cp ../NetApp-ansible-roles/na_ots_deploy . -r`

- Edit the `inventory.txt` file with ESX cluster information and choose a Deploy VM name and IP in this section:
```
[ontap_deploy]
OntapDeploy-Ansible     ansible_host=<OntapDeploy_IP>
```

- Edit `vars/vars_deploy.yml` with your environment variables.
- Edit `vars/vars_deploy_pwd.yml` with your ESX and Ontap Deploy passwords.

**Run the playbook:**
```
ansible-playbook -i inventory.txt ontap-deploy-install.yml
```

Access to Ontap Deploy typing **https://<OntapDeploy_IP>** in your browser with username and password used in the vars files.

----
## How to create a new Ontap Select cluster

Be sure that `na_ots_cluster/` role is installed in the repository. `cp ../NetApp-ansible-roles/na_ots_cluster . -r`

- Edit the `inventory.txt` file with ESX cluster and Ontap Deploy information.
- Edit `vars/vars_cluster.yml` with your environment variables.
- Edit `vars/vars_cluster_pwd.yml` with your Vcenter and Ontap passwords.

**Run the playbook:**
```
ansible-playbook -i inventory.txt ontap-cluster-create.yml
```

The new Ontap Select cluster will appear in the Ontap Deploy Dashbord.
It's possible to access to Ontap Select typing **https://<Ontap_Select_IP>/sysmgr/** in your browser with username and password used in the vars files.


----
# LICENSE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

