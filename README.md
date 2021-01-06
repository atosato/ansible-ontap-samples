# Ansible playbook samples for NetApp Ontap
----
This repository contains Ansible playbook to automate some tasks in a NetApp ONTAP 9 environment.

To try these samples you can use an Ontap Select VM for testing (90 days evaluation license is provided with the image).

As a quick setup guide follow these steps:
Clone this github repository:
```
git clone https://github.com/atosato/ansible-ontap-samples.git ansible-ontap-samples
```

Create a Python virtual environment:
```
python3 -m venv venv
source venv/bin/activate
pip3 install --upgrade pip setuptools wheel
pip install pip-tools
pip-sync
```
If you want to update the requirements libs version:
```
pip-compile requirements.in
pip-sync
```

To use these playbooks you need to download the **NetApp Ansible ONTAP collection**: <link>https://github.com/ansible-collections/ansible_collections_netapp</link>.
```
ansible-galaxy collection install netapp.ontap
```

**Tested with:**
 - Ansible:
    * 2.9.9
    * 2.9.6
 - Ansible Collections:
    * 20.5.0
    * 20.3.0
 - Ontap Deploy OVA:
    * ONTAPSELECT9.7.ova
    * ONTAPdeploy2.12.1.ova


----
# LICENSE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
