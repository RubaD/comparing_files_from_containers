# comparing_files_from_containers

There is two playbooks :

- copy_from_containers.yml which is used to copy files from containers on remote hosts to the localhos
- compare_all_files.yml which used to compare different files.
### How it works
copy_from_containers.yml : at first it includes the file that containes the neede informationsabout the containers and the files that will be copied (containerss.yml), then it gets the seconttext of the original file in the containers , copy these files from the containers to the remote hosts ( where the contaniers are) and then uses fetch module to copy these files and set the secontext as the original file.
compare_all_files.yml : fisrt two lists are created to store any chnages between the files, then the compare_2_files.yml which has the tasks the compare the files is included, in compare.yml template module was used with dry run and diff to collect the needed data about the files ( checksum , selinux , owner and group) these data was compared and if there is any change, these chnages will be added to the lists , in case there is a content change copy module with dry run and diff was used to display the difference.
### How to use
- copy.yml takes location variable as an arguemnt and it is where to copy the files.
- compare_all_files.yml takes two varibale: first_dir , sec_dir as arguments and these where are the files that will be compared.
