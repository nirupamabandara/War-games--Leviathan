# War-games--Leviathan

Name: Nirupama Bandara

Registration Nyumber : MS13961718

#Step1
Leviathan – Level 0

Leviathan’s levels are called leviathan0, leviathan1, etc. and can be accessed on leviathan.labs.overthewire.org through SSH. Data for the levels can be found in the homedirectories.

To login to the first level use:

Username: leviathan0

Passowrd: leviathan0

SSH Connection Image:

Username: leviathan1

Password: rioGegei8m

![1 putty](https://cloud.githubusercontent.com/assets/12378369/7900272/82e99d6c-0769-11e5-85d9-63afeb8d73a9.PNG)

![2 loggedlevel0](https://cloud.githubusercontent.com/assets/12378369/7900275/9f08149c-0769-11e5-9b96-f65c53a37372.PNG)

![3 level0backup](https://cloud.githubusercontent.com/assets/12378369/7900276/a1db4dc4-0769-11e5-90ab-b27c12e62c70.PNG)

#Step2
Leviathan – Level 1

Username: leviathan1

Password: rioGegei8m

#Step2.1 Access level 2

Leviathan – Level 1

Leviathan 1 presents us with a binary in our home directory.  If we run it we see that is a utility that ask and checks for a password. Knowing this, the binary is either reading the correct password from somewhere else or has it stored within the binary. In this case, the password is stored within the binary. We need to trace the binary. Many of you might catch the small hint to the movie Hackers within the binary. When Plague states the 4 most common passwords are love, sex, secret, and god.
Username: leviathan2

Password: ougahZi8Ta

![4 level1](https://cloud.githubusercontent.com/assets/12378369/7900673/7d8b5968-0783-11e5-9477-89ed1244d4c8.PNG)

To see what functions it is calling let’s use “ltrace”.We can see it is using strcmp() to check if an entered password is the same as it's stored string, "sex". Running the binary again we can now try entering "sex" as the password to test what will happen

![5 level1](https://cloud.githubusercontent.com/assets/12378369/7900682/a7ede018-0783-11e5-9f5c-962ff4ac46e7.PNG)

#Step3
Leviathan – Level 2

Leviathan2 presents us with a small binary that belongs to the user leviathan3 and group leviathan2. The program contains a small security hole that can be exploited using a symbolic link.  To understand how the program functions at its core and what is happening behind the scenes when the program executes, we will use a few Linux commands and techniques to enlighten us with this information.
Username: leviathan3
Password:Ahdiemoo1j

When you run "printfile" we can see that it wants a file path argument. We are going to go ahead and create a directory and a file with a space in the name.

![6 loggedlevel2](https://cloud.githubusercontent.com/assets/12378369/7900691/e59d51e6-0783-11e5-8db6-09925c52ae7f.PNG)

So, what is happening here is a small security hole in how this program functions. We can see that the function access() and /bin/cat are being called on the file. What access() does is check permissions based on the process’ real user ID rather than the effective user ID.
While access does use the full file path, the cat on the file is not using the full file path. We can see this near the end of the output where /bin/cat/ is being called to tmp.txt as if it were a separate file, it’s really the second half of our filename. This can be exploited if we create a symbolic link from the password file to the file we created in /tmp.
Let’s create the symbolic link, but with only the first part of the filename we created before the space. Issue the command ls –al; we see file tmp.txt was not converted to a symlink, but a separate symlink called "file" was created.

![7 level2](https://cloud.githubusercontent.com/assets/12378369/7900695/29d5d40a-0784-11e5-93dd-c547c5cafc60.PNG)

![8 loggedlevel3](https://cloud.githubusercontent.com/assets/12378369/7900716/636f8be8-0784-11e5-9bde-7947eeb0a938.PNG)

#Step4
Leviathan – Level 3

For Leviathan 3, the process is fairly simple.  We only need a few commands that we are already familiar with to get access to Leviathan4’s shell. When we finally do get his shell, we can cat his password in /etc/leviathan_pass/leviathan4 and correctly log in as him to begin level 4->5. 

Username: leviathan4

Password: vuH0coox6m

The point of interest for us will be the snlprintf word. Right after that you see the words, "You've got shell!” Let's use that as the password.

![8 1level3](https://cloud.githubusercontent.com/assets/12378369/7900724/d4fab1ca-0784-11e5-8876-84a802fecd72.PNG)

#Step5
Leviathan – Level 4

Username: leviathan5

Password:Tith4cokei

![9 level4](https://cloud.githubusercontent.com/assets/12378369/7900728/0608a8c6-0785-11e5-9f7e-eb891067ea17.PNG)

![10 convertbinarytoascii](https://cloud.githubusercontent.com/assets/12378369/7900730/25501a5c-0785-11e5-9347-c6f0b9ca2cd6.PNG)

#Step6
Leviathan – Level 5

Username: leviathan6

Password: UgaoFee4li

![11 level5](https://cloud.githubusercontent.com/assets/12378369/7900731/287befda-0785-11e5-90b6-806d9927da17.PNG)


![12 runlevel5](https://cloud.githubusercontent.com/assets/12378369/7900738/65386750-0785-11e5-9323-9f9e20548bed.PNG)

#Step7

Leviathan – Level 6

Username: leviathan7

Password:ahy7MaeBo9

![13 level6](https://cloud.githubusercontent.com/assets/12378369/7900740/68dd8728-0785-11e5-8bfd-14b0b04a70d1.PNG)

![14 runlevel6](https://cloud.githubusercontent.com/assets/12378369/7900741/85c84512-0785-11e5-840c-dc5a7444e54d.PNG)

![15 chmod](https://cloud.githubusercontent.com/assets/12378369/7900742/8c57afbc-0785-11e5-843a-3aa9113609ef.PNG)

![16 bruteforce](https://cloud.githubusercontent.com/assets/12378369/7900745/9103adcc-0785-11e5-891a-af82be90d346.PNG)

Run the binary and simply wait for it to iterate through all possible number combinations. Note that we could echo out the password when we find it. Here the script will simply input the pass to the binary and pop us into leviathan7’s shell when it finds a match.


![17 script](https://cloud.githubusercontent.com/assets/12378369/7900746/94b96d4e-0785-11e5-9fdb-3bb2b884376c.PNG)

#Step8

Leviathan – Level 7

![18 level7](https://cloud.githubusercontent.com/assets/12378369/7900750/c9f9a94c-0785-11e5-931b-2c55db7ce28c.PNG)







