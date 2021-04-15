# Ontap - Ansible playbook samples
----
This repository contains Ansible playbooks helping to automate the creation of an CIFS SVM (vserver) DR and an SVM Clone to check if the Disaster Recovery replicas are working fine..

Edit vars with the ONTAP cluster information: vars/vars_demo.yml
Edit vars with the ONTAP cluster Login information: vars/vars_demo_login.yml

### Create production NAS SVM:
```
ansible-playbook 01_create_svm_nas.yml
```
The playbook create an SVL with one volume and a share named Vol_Data.

### Create SVM DR:
```
ansible-playbook 02_create_svm_DR.yml
```
The default behaviour will create an SVM DR using a different "identity" and a new data IP.
You could use the TAG preserve-identity to create an SVM DR with same name and IP of the source.
```
ansible-playbook 02_create_svm_DR.yml --tags preserve-identity
```


### Requirements:
To use these playbooks a snapshot named **daily.0** must exist in each svm_src volume on production SVM.
Ontap could automatically schedule daily.0 creation changing the dafault naming convention:
```
cluster> vol modify -volume <vol_name> -vserver <svm_src> -sched-snap-name ordinal
```

### Create a cloned SVM to test the DR environment:
```
ansible-playbook 03_create_svm_DR_clone.yml
```

### Delete the cloned SVM:
If the clone is created in a test environment you could use the following playbook to delete all Volumes and Shares existing in svm_clone:

**WARNING: POSSIBLE DATA LOSS!!! - This playbook delete all the data present in the target SVM - Use it in a TEST environment ONLY**
```
ansible-playbook 93_DELETE_svm_DR_clone.yml
```

----
# LICENSE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
