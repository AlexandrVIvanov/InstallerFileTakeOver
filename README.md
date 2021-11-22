# InstallerFileTakeOver


For your notes, this works in every supporting windows installation. Including Windows 11 and Server 2022.

As some of you might notice, this also work in server installations. While group policy by default doesn't allow standard users to do any msi operation. The administrative install feature thing seems to be completely bypassing group policy.

This variant was discovered during the analysis of CVE-2021-41379 patch. the bug was not fixed correctly, however, instead of dropping the bypass. I have chosen to actually drop this variant as it is more powerful than the original one.

I have also made sure that the proof of concept is extremely reliable so it works in every attempt. The proof of concept overwrite Microsoft Edge elevation service DACL and copy itself to the service location and execute it to gain elevated privileges. While this technique may not work on every installation, because windows installations such as server 2016 and 2019 may not have the elevation service. I deliberately left the code which take over file open, so any file specified in the first argument will be taken over with the condition that SYSTEM account must have access to it and the file mustn't be in use. So you can elevate your privileges yourself.

The best workaround available at the time of writing this is to wait Microsoft to release a security patch, due to the complexity of this vulnerability. Any attempt to patch the binary directly will break windows installer. So you better wait and see how Microsoft will screw the patch again.

Final note, while I was working on CVE-2021-41379 patch bypass. I was successfuly able to product 2 msi packages, each of them trigger a unique behaviour in windows installer service. One of them is the bypass of CVE-2021-41379 and this one. I decided to actually not drop the second until Microsoft patch this one. So Be ready !
