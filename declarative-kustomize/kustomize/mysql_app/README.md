# mysql_app

This is app based on kustomize.
The folder structure is as per kustomize recommendation.

## Base

This folder has all files which all not change irrespective of your environment. But it cannot work independly because it is needs secrets which is defined in individual folder.
There should be no patches in the base folder, so that the content can be considered to be an untainted set of files to which patches can be applied by overlays.
Namespaces should NOT be directly referenced in base assets such that the content can be applied to any namespace.

## Overlays

This folder has production, testing and development folder
e.g. testing folder, you will see `kustomization.yaml` file which is just creating a secret for testing environment
on the other hand, Production folder has a secret, which is very specific to production environment.

In short, this is very basic example of kustomization, no patching is involved here. But the idea is, if you wish to have separate secret for the environment,
you must create them in the kustomization file in respective environment. You should NOT add or create this part in main kustomization.yaml file which is under base folder.qq
