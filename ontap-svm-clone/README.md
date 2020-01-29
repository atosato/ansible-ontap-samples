# Ontap - Ansible playbook samples
----
This repository contains Ansible playbooks helping to automate the creation of an CIFS SVM (vserver) clone.

The playbook: **ontap-svm-volume_and_shares-clone.yml** read all volumes and shares from a SVM (svm_src) and will recreate them to another SVM (svm_clone)

To use these playbooks a snapshot named **hourly.0** must exist in each svm_src volume.
Ontap could automatically schedule hourly.0 creation changing the dafault naming convention:
```
cluster> vol modify -volume <vol_name> -vserver <svm_src> -sched-snap-name ordinal
```

Edit vars with the ONTAP cluster information:
```
vars:
  svm_src: "svm-src-name" #<- SVM Source name or IP
  svm_clone: "svm-clone-name" #<- SVM Clone name or IP
  login: &login
    hostname: "xx.xx.xx.xx" #<- ONTAP Cluster MGMT IP
    username: "admin"
    password: "password"
```

To clone Volumes and Shares from svm_src to svm_clone:
```
ansible-playbook ontap-svm-volume_and_shares-clone.yml
```

If the clone is created in a test environment you could use the following playbook to delete all Volumes and Shares existing in svm_clone:
**WARNING: POSSIBLE DATA LOSS!!! - This playbook delete all the data present in the target SVM - Use it only in a TEST environment**
```
ansible-playbook ontap-svm-clone-delete.yml
```

----
# LICENSE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
