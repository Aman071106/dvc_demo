Data Version control:

Actually it manages the versions of data we have whether it is images,audio ,video,text.


📁 GitHub
Version control for:

Code (e.g., model training, data pipelines)

Configs and scripts

CI/CD workflows

Collaboration across teams

Audit trails for changes

📦 DVC
Version control for:

Large datasets (training, testing)

Model artifacts (.pt, .pkl, etc.)

Reproducible ML pipelines

Experiments tracking and comparison

Stores metadata in Git, but data in S3, GCS, etc.


Commands:
1.dvc init and git init
Similar to git init
The `.dvc` folder will contain the config file for remote data configuration which will be seeing through a project.

As we run git init :
these files will be auto tracked and require commit 
        new file:   .dvc/.gitignore
        new file:   .dvc/config
        new file:   .dvcignore
2. so commit them
3. The data.txt.dvc file will store the hashkey and gitignore should contain the data.txt
4. The data.txt is tracked by dvc and can be also taken to remote repo or cloud service.(see later)
5. To switch to specific data version we check git log and then swoitch to that commit
git checkout <commit-hash>
(DETACHED HEAD STATE:

M       data.txt.dvc
Note: switching to '17e47cb086c4eca97969aae78afe39e88f60ef32'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 17e47cb first data
)
this will show us that commit in the same branch which is noot safer.
So we should use git checkout -b newBranchName <commit-hash>

Then dvc checkout to view the data.txt or any other data source at that specific commit.
