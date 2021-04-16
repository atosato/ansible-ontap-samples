# Ontap - Ansible playbook samples to create CIFS Shares from CSV file
----
This repository contains Ansible playbooks helping to automate the creation of an CIFS Shares from CSV file.

The playbook: **ontap-svm-cifs_shares-create-from_csv.yml** read all shares from a CSV file and create them to a specific **svm_target** SVM.


Edit vars with the ONTAP cluster information: vars/vars_cifs_shares-create-from_csv.yml
```
  svm_target: "svm-target-name" <- All Shares will be created in this SVM
  cifs_shares_cvs: "vars/cifs_shares.csv" <- CSV Shares file to be populated
  hostname: "xx.xx.xx.xx" <- ONTAP Cluster MGMT IP
  username: "admin"
  password: "password"
```

Populate the CVS using the following format: vars/cifs_shares.csv
```
Share,Path
admin$,/,
c$,/,
ipc$,/,
share_name,/vol_name/folder_name
```

### Create CIFS Shares from CSV file:
```
ansible-playbook ontap-svm-cifs_shares-create-from_csv.yml
```

----
# LICENSE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
