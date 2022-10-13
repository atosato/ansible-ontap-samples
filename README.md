# Ansible playbook samples for NetApp Ontap
----
This repository contains Ansible playbooks to automate some tasks in a NetApp ONTAP 9 environment.

To try these samples you can use Ontap Selelect, a 90 days evaluation license is provided with the image.

For a quick repository setup follow these steps.

Clone this github repository:
```
git clone https://github.com/atosato/ansible-ontap-samples.git ansible-ontap-samples
```

Create a Python virtual environment:
```
python3 -m venv venv
source venv/bin/activate
pip3 install --upgrade pip setuptools wheel
pip3 install pip-tools
pip-sync
```
If you want to update the requirements libs version:
```
pip-compile requirements.in
pip-sync
```

To use these playbooks you need to install the **NetApp Ansible ONTAP collection**: <link>https://github.com/ansible-collections/ansible_collections_netapp</link>.
```
ansible-galaxy collection install netapp.ontap

To install a specific release:
ansible-galaxy collection install netapp.ontap:21.24.1
```

**Tested with:**
 - Ansible:
    * 2.13.5
 - Collection:
    * netapp.ontap 21.24.1
 - Ontap Select:
    * ONTAPSELECT9.11.1GA.ova


----
# LICENSE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
