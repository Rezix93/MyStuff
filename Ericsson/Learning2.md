1. 
```
cd ~/research/eclipse  
 WEBKIT_DISABLE_DMABUF_RENDERER=1 ./eclipse
```
. I opened the TC and lots of Erros
   How to solve it: 1. look at erros: We see somthing like java and permission and we undestarnd
   This is regarding to running java in sudo mode already ->
   2.1. We have to remove build files
   2.2 back to TC and clean the project

3. For having Trace compass Do no download the file and Import it. sync it from Github.

`File -> import -> git > Project from Git -> Existing local repossitory`

![image](https://github.com/user-attachments/assets/877d0f83-de1b-4011-b9e2-847d85ac3c90)
![image](https://github.com/user-attachments/assets/9c60d238-d445-4a17-825b-873702b604e0)

5. WIF request: 
[https://ewaguest.portal.amcs.ericsson.net/]
6. To sign an ECA:
Create an account with the Eclipse Foundation if you have not already done so;
Sign a ECA.
Log into the Eclipse Contributor Agreement page;
Complete the form.
An Eclipse Account will grant you access to Gerrit, Bugzilla, and other Eclipse Foundation web resources.
Use the same account to contribute to Eclipse, LocationTech, and PolarSys projects.
7. Email:  https://outlook.office.com/mail/
8. https://accounts.eclipse.org/users/rezix/edit
9. Git notes:
```diff
+ When you push something but do not like it: - git push -d
+ When get updated the project:  - When you hear on meet we had a new big update. Then it is good time not eveyday. not nessesary
+ Remove Branch? - Wait till merge. then it suggest to be removed
```

10. Java
```  
sudo update-alternatives --config java
sudo update-alternatives --set java /usr/lib/jvm/java-21-openjdk-amd64/bin/java 
source ~/.bashrc
```
11. In 
```
- if (counter instanceof CounterAspect)
+ if (counter instanceof ITmfCounterAspect)

```

# Flexibility and Abstraction:

Using an interface (ITmfCounterAspect) instead of a class (CounterAspect) provides more flexibility and abstraction. It allows the counter variable to refer to any object that implements the ITmfCounterAspect interface, not just objects of the CounterAspect class.

```diff
- CounterAspect counterAspect = (CounterAspect) counter;
+  ITmfCounterAspect counterAspect = (ITmfCounterAspect) counter;
```
12. 
conforml commits in Github: 
```                                     
counter.core: Generalize the counterAnalysis to take ITmfCounterAspect

[Changed] Allowed ITmfCounterAspect populate counterAnalysis  
```

13. Before one new push, get the lates version of project: `git rebase`
### Rebase Regularly
To keep your feature branch up-to-date with the latest changes from the base branch (like main or master), you should rebase regularly:
```
2012 git fetch --all
2013 git rebase rezaGithub/master 

2018 git fetch --all
2019 git rebase origin/master counterAspectChanges 
```

after change code from reviewers: 
```
git commit --amend 
git push rezaGithub counterAspectChanges -f

```


14. 

Now that it overrides, you can remove the Javadoc here, the one from interface will be used. So javadoc here should be removed.
```
/**
 * Get the groups
 *
 * @return the groups
 */
@Override
public Class<? extends ITmfEventAspect<?>>[] getGroups() {
    return fGroups;
}
```
