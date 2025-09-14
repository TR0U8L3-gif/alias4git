# Share git aliases across multiple users/workstations

## Set up steps -  

1. Clone this repository 
   ```
   git clone https://github.com/pipelineinc/alias4git.git
   ```
2. Locate global .gitconfig file location on your machine -

   Default on macos machine is home directory ( ~ )
   Default on windows machine is home directory ( %USERPROFILE% )
      
   ![Alt text](image_gitconfigpaths.png)
4. Update contents of your global .gitconfig to below - 
```
# replace file paths below with matching filepaths from cloned alias4git repository
[include]
   path = <path\\to\\alias4git\\alias.gitconfig> 	# make sure to remove '<' and '>'

[alias]
	cfg = !git config --file <path\\\\to\\\\alias4git\\\\alias.gitconfig>
	cfg-update = "!f() { orig_dir=\"$PWD\" && cd <path\\\\to\\\\alias4git> && git pull && cd \"$orig_dir\"; }; f"
	
[user]
	email = <your-email>
	name = <your-name>
	
```

1. Update alias.gitconfig path to appropriate path of cloned alias4git repository

## How to add new alias and share across team -
1. Follow setup steps mentioned above
2. Open command prompt 
3. Change current directory to alias4git repository
   ```
   cd path\to\alias4git
   ```
4. Add new alias using command -
	```
	git cfg alias.st "status"
	```
	instead of 
	```
	git config --global alias.st "status"
	```
5. Check if newly added alias is visible in list 
   ```
   git cfg -l
   ```
   or using 
   ```
   git cfglist
   ```
6. Commit your change to this repository using git and create Pull Request
   ```
   git add .
   git commit 
   git push
   ```
7. Ask your team to sync alias4git repository by pulling new changes
   ```
   git pull
   ```


