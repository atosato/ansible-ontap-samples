# Ontap - Ansible playbook samples
----
Ansible playbooks to automate SVM creation, replicate it on a different storage and clone it to Test the DR procedure.

Edit vars file and fill values with your environment information: vars/vars_demo.yml
Edit vars file Login information: vars/vars_demo_login.yml

### Create production NAS SVM on ONTAP Cluster A:
This playbook create an SVM with one Volume and a Share named "Vol_Data".
```
ansible-playbook 01_create_svm_nas.yml
```

### Create SVM DR on ONTAP Cluster B:
This playbook create a new SVM on DR storage an mirror all Volumes, Shares and ACL
```
ansible-playbook 02_create_svm_DR.yml
```
The default behavior will create an SVM DR using a different "identity" and a new data IP is required.
The SVM with a new Identity could be started and used to access replicated data in Read-Only.
You could use the TAG preserve-identity to create an SVM DR with same name and IP of the source.
```
ansible-playbook 02_create_svm_DR.yml --tags preserve-identity
```

### Create a Snapshot on production to be cloned on DR:
This playbook create a new Snapshot on all production Volumes and will update the mirror to replicate them on DR.
```
ansible-playbook 03_create_svm_nas_snapshots_and_update_mirror.yml
```

### Create a cloned SVM to test the DR environment:
To test the DR environment accessing data in Read-Write is possible to Clone the SVM-DR using the following playbook:
```
ansible-playbook 04_create_svm_DR_clone.yml
```

### LAB Cleanup - Delete ALL the SVMs:
**WARNING: POSSIBLE DATA LOSS!!! - This playbook delete all the data present in the target SVM - Use it in a TEST environment ONLY**
DELETE SVM DR Clone on ONTAP Cluster B:
```
ansible-playbook 94_DELETE_svm_DR_clone.yml
```

DELETE SVM DR on ONTAP Cluster B:
```
ansible-playbook 92_DELETE_svm_DR.yml
```

DELETE production SVM on ONTAP Cluster A:
```
ansible-playbook 91_DELETE_svm_nas.yml
```

----
# LICENSE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
