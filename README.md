# Ontap Select - Ansible playbook samples
----
This repository contains samples playbook helping to automate the creation of an Ontap Select SDS cluster.

To use these playboos you need to download the NetApp Ansible roles repository: <link>https://github.com/NetApp/ansible</link> and an Ontap Deploy OVA image.

Tested with:
 - Ansible 2.8.5
----
## How to install Ontap Deploy

Place your Ontap Deploy OVA image in OntapSelectOVA folder:
'cp ONTAPdeployX.Y.Z.ova OntapSelectOVA/.'

Edit the inventory.txt file with EXS information.
Use a Deploy VM name and IP of you choice in this section:
'''
[ontap_deploy]
OntapDeploy-Ansible     ansible_host=<OntapDeploy_IP>
'''

Edit vars/vars_deploy.yml with your environment variables.
Edit vars/vars_deploy_pwd.yml with your ESX and Ontap Deploy password.

Be sure that 'na_ots_deploy/' role is installed in the repository.

Run the playbook:
'ansible-playbook -i inventory.txt ontap-deploy-install.yml'

(TODO) ## How to create a new Ontap Select cluster

# LICENSE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

