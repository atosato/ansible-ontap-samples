# Ontap Select - Ansible playbook samples
----
This repository contains Ansible playbooks helping to automate tasks in a NetApp Ontap 9 Environment.

Could be useful to use an Ontap Select cluster for testing purpose (90 days evaluation license is provided with the image).

Clone this playbooks repository:
```
git clone https://github.com/atosato/ansible-ontap-select.git ansible-ontap-select
```

To create Python virtual environment follow these steps:
```
python3 -m venv venv
source venv/bin/activate
pip install pip-tools
pip-compile requirements.in
pip-sync
```

To use these playbooks you need to download the **NetApp Ansible collection repository**: <link>https://github.com/ansible-collections/ansible_collections_netapp</link>.
```
ansible-galaxy collection install netapp.ontap
```

**Tested with:**
 - Ansible:
    * 2.8.5
    * 2.9
 - Ansible Collections:
    * 20.2.0
 - Ontap Deploy OVA:
    * ONTAPdeploy2.12.1.ova
    * ONTAPSELECT9.7RC1.ova


----
# LICENSE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
