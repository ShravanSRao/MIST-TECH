<h2>1)Over The Wire</h2>
<br>
<h3>My experience</h3>
<br>
<p>This activity pushed me to learn Linux commands, which I had been lazy to learn, even though I had dual-booted my system before the meet was conducted. I used to just run to ChatGPT and use it to try and solve CTF questions, but I gained some confidence after completing this task. I have completed 12 questions so far, and I hope to continue. I will be documenting my initial thought process and how I tackled each question. I have checked solutions for some of them on YouTube when I got stuck </p>

<h3>Question 1: Level 0→ Level 1</h3>
<p>Just opened a file so nothing noteworthy.I used less to open the text file </p>
<b>Flag found</b>=ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If<br>
<b>The syntax</b><code>less readme</code>

<h3>Question 2: Level 1→ Level 2</h3>
<p>I knew the ls, cd, and find commands, so as I learned cat, du, and file through these questions, I did some googling. I learned that to open a file that starts with a -, we have to use ./ before it and then run the simple command, which helped me get the correct answer.</p>
<b>Flag found</b>=<code>263JGJPfgU6LtdEvgfWU1XP5yac29mFx</code><br>

<b>The syntax</b><code>cat ./-</code>

<h3>Question 3: Level 2→ Level 3</h3>
<p>The file had spaces between so just googled how to open those file .I learned that i have to put the file name inisde <code>"File name"</code></p>
<b>Flag found</b>=<code>MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx</code><br>
<b>The syntax</b>
<ul>
  <li><code>file "spaces in this filename"</code></li>
  <li><code>cat "spaces in this filename"</code></li>
</ul>
<h3>Question 4: Level 3→ Level 4</h3>
<p>I learned that files hidden started with a dot <code>.file_name</code>so i used <code>ls -f</code> it showed the hiden ASCII file named <em>...Hiding-From-You  .  ..</em>i tried using the format <code>cat "...Hiding-From-You  .  .."</code> but it didn't work for some reason so i used nano command</p>
<b>Flag found </b>=<code>2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ</code><br>
<b>The syntax  : </b><code>nano ...Hiding-From-You  .  .. </code>

<h3>Question 5: Level 4→ Level 5</h3>
<p>Used <code>file ./-fileXX </code>repeated this operation 7 times to find that the -file07 is ASCII format opened  it and found the flag.Later on relaised i could have used find command with -size operator to find files based in file size.Here i just used brute force trying to open all files</p>
<b>Flag found</b>=<code>4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw</code><br>
<b>The syntax</b>
<ul>
  
  <li><code>file ./-fileXX</code></li>
  <li><code>cat ./-file07</code></li>
  
</ul>

<h3>Question 6: Level 5→ Level 6</h3>
<p>My intial thoughts were that there is probably a hidden file and listed all the files so i used <code>du -h</code> which lists the size of all the files .I misjudged that K represents bits and <b>. file </b>of 1.3M <em>[I assumed M was bytes :( ]</em> size was the targeted file which we i was supposed to open.Thats the reason i was stuck for a long time then later on checked youtube to get the solution .
<ul>
  <li>I learned that ./ refers to the current directory </li>
  <li>cd .. to come out of the current directory </li>
  <li>Use the documentation to search for things like operators</li>
</ul></p>
<b>Flag found</b>=<code>HWasnPhtq9AVKe0dmk45nxy20cvUa6EG</code><br>
<b>The syntax</b>
<ul>
  <li><code>find ./ -size 1033c</code> </li>
  <li><code>cat ./maybehere07/.file2</li>
</ul>
<h3>Question 7: Level 6→ Level 7</h3>
<p>After learning from my previous mistake,i read find = documentation to find user an ddgroup name oeprators,But i was running find <code>./ -user bandit7 -group bandit6 -size 33c</code> but it returned nothing and my terminal was glitching later on tired ls to list files but there were non.I restarted the terminal thinking there was some glitch .I got stuck again so i again went to Hasan-AL-Gaib youtube and got to know i was supposed to use <code> / </code> to search server so  stopped youtube and ran the command.Started getting  persmission denied  error went back to youtube thinking i did something wrong .It was said that im supposed to add <code>2>/dev/null</code> at the end it was told it moves all the permission denied to this file 
<br>  <b>Unclear : </b>I still dont quite understnad it </p>
<b>Flag</b>=<code>morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj</code>
<b>The syntax</b>
<ul>
  <li><code>find / -user bandit7 -group bandit6 -size 33c 2>/dev/null</code></li>
</ul>
<h3>Question 8: Level 7→ Level 8</h3>
    <p>Learned grep command which used to recognize text patterns from some oggogle searches .-w operator of grep searches for whole words so i got through this level without wasting muh time</p>
<b>Flag</b>=<code>dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc</code><br>
<b>The syntax</b>
<code>grep -w "millionth" data.txt</code>

<h3>Question 9: Level 8→ Level 9</h3>
<p>I tried using <code>uniq -c data.txt</code> but no use so i started googling methods and stumblled upon <code>sort file.txt | uniq -c</code> and used this .sort uses whitespace as delimiter and sorts them,pipe operator takes the uoutput from lhs and gives it to the rhs and the uniq -c counts each apperance.Later on i realised i could use uniq -u which gives the string which appears only once </p>
<b>Flag</b>=<code>4CKMh1JI91bUIZZPXDqGanal4xvAg0JM</code><br>
<b>The syntax</b>
<code>sort data.txt | uniq -c</code>
<h3>Question 10: Level 9→ Level 10</h3>
<p>I saw that the page recommended search base64 ,in my biasness when i tired opening the file whihc was in unknown format i assumed it was base64.So with half baked knowledge instead of giving the command <code>base64 -d data.txt</code> i was using <code>base64 data.txt</code>.
I  now (While writing this writeup) realiz that I  was converting bizare text to base64 but when trying to clear the level,I actually thought i was decoding it then used <code>base64 data.txt | uniq -u</code>But as my inital assumptions were wrong it didnt lead anywhere.So i again turns towards Youtube Sensei to get the solution and got the solution </p>
<b>Flag</b>=<code>FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey</code><br>
<b>The syntax</b>
<code>sort data.txt | Strings | uniq -c</code>


<h3>Question 11: Level 10→ Level 11</h3>
<p>Since i tried using base64 i knew how to decode and this was the quickest solve out of all problems</p>
<b>Flag</b>=<code>dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr</code>


<b>The syntax</b>
<code>base64 -d data.txt</code>

<h3>Question 12: Level 11→ Level 12</h3>
<p>I tried some simpel goggle searches and got the command. Learned the tr commands which can be used to perform Rot-13 decrypting</p>
<b>Flag</b>=<code>7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4</code><br>
<b>The syntax</b>
<code>cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'</code>

<h3>Question 13: Level 12→ Level 13</h3>
<p>This was the most irritating out of the questions i solved.I got stuck and went to Lord youtube and solved the program.It was frustrating because even though i my just unzipping files but i had to do it so many times ,it was irritating .But atleast i will remember it for a longer time . i learned how cp,>operator </p>
<b>Flag</b>=<code>FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn</code>
<b>The syntax</b>
<ul>
  <li><code>mkdir /tmp/s</code></li>
  <li><code>cp data.txt /tmp/srao</code></li>
  <li><code>xxd -r data.txt > data</code></li>
  <li><code>file data</code></li>
  <li><code>mv data data.gz</code></li>
  <li><code>gzip -d data,gz</code></li>
  <li><code>file data</code></li>
  <li><code>mv data data.bz2</code></li>
  <li><code>bzip2 -d data.bz2</code></li>
  <li><code>mv data data.tar</code></li>
  <li><code>tar xvf data.tar</code></li>
  <li><code>mv data5.bin data.tar</code></li>
  <li><code>tar xvf data.tar</code></li>
  <li><code>mv data6.bin data.bz2</code></li>
  <li><code>bzip2 -d data.bz2</code></li>
  <li><code>mv data data.tar</code></li>
  <li><code>tar xvf data.tar</code></li>
  <li><code>mv data8.bin data.gz</code></li>
  <li><code>gzip -d  data.gz</code></li>
  <li><code>file data</code></li>
  <li><code>cat data</code></li>
  
</ul>

