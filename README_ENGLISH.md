<h3 p align="center" > <i>Forgive me for any grammatical errors, English is not my native language. </i> </h3></p>

<h2 p align="center" > STREAMS </h2></p>

## Step 1 - STANDARD INPUT (STDIN).

<p> - Usually STDIN is data input by keyboard keys, but it can also be recognized by <b>"0<"</b> or just <b>"<" </b> which can be used to pass files as input instead of the standard input.
</p>

![Passo 1](img/Passo_1.png)

<p> - In practice it is as if we had used the command <b>"cat numeros"</b>, but in this example we use the file numeros as input for the cat. </p>

![Passo 2](img/Passo_2.png)

<p> - We can use other commands that expect an input, for example, <b>sort</b>. </p>

![Passo 3](img/Passo_3.png)

<p> - The flow can be continued with other output structures such as pipe. In the example sorting the numbers and not showing repetitions. </p>

## Step 2 - STANDARD OUTPUT (STDOUT).

<p> - We can identify STDOUT as the successful output, also identified by the commands <b>"1>"</b> or <b>">"</b>, where through an input we direct it with the objective of a successful output.</p>

![Passo 3_1](img/Passo_3_1.png)

<p> - STDOUT differs from STDERR which we will talk about later, to recognize a successful output outside a script we can use the command "echo $?" right after a command. </p>

![Passo 5](img/Passo_5.png)

<p> - When the output of the command <b>"echo $?</b> be <b>"0"</b> shows that the command was successful, being a STDOUT. Any number other than 0 is an error output (STDERR). </p>

<p> - Note that we use <b>></b> to overwrite a file and <b>>></b> to add something one line below the targeted file. </p>

![Passo 6](img/Passo_6.png)

<p> - In this example the first time we use the cat command on the saida.txt file our output is "abcd". </p>

<p> - It can be seen that by using the <b>">"</b> with the values 123 we overwrite the previous contents of the file and its new output with cat is "123".</p>

<p> - Already using <b>">>"</b> with the content "abcd", we can see that we have added this new text below the last existing content in the saida.txt file.
<p> - Your new exit is: <br>123<br>abcd<br></p>

## Step 3 - STANDARD ERROR (STDERR).

<p> Any output that results in an error is considered an STDERR. </p>

![Passo 7](img/Passo_7.png)

<p> - In the first command "ls" we have a successful output, showing the files in the directory we are in. </p>
<p> - Now in our second command we use the "-j" flag, which does not exist, giving us an error output. </p>

![Passo 8](img/Passo_8.png)

<p> - We use the <b>2></b> to redirect the error output to a file. Similarly to STDOUT, we can use <b>2></b> and <b>2></b>, to overwrite and add respectively. </p>

## Step 4 - REDIRECTING OUTPUTS.

<p> - In the following example I created a simple script with the following content: <br><br>
echo "Hello"<br>
ls -j<br> </p>

<p> - When running it we will have both outputs, STDOUT and STDERR. </p>

![Passo 9](img/Passo_9.png)

<p> - If we try to redirect the output as STDOUT to a file, we would have a problem. </p>

![Passo 10](img/Passo_10.png)

<p> - Notice that by directing the output of the script to the output.txt file we still have the error as the output of the command, and by using cat in the saida.txt file we notice that only the successful output was saved inside it. </p>

![Passo 11](img/Passo_11.png)

<p> - We can have the opposite result using a STDERR output "2>", now the content of an error output was saved in the file saidaerr.txt and the successful output appeared in the terminal being the string "Hello". </p>

<p> - But how can we save both outputs in one file, or better save each output in its respective type. </p>

<p> - We can use the following logic. </p>

![Passo 12](img/Passo_12.png)

<p> - If you want to save both outputs in one file we only use the following structure: "./script.sh > saida_and_saida_err.txt, where the content of the successful output is directed to the file in question and at the end of the syntax I am asking for the error output to also be directed to the successful output with the command <b>2>&1.</b>" </p>

<p> - This way with the cat command we can see that we have saved both types of output in one file. </p>

![Passo 13](img/Passo_13.png)

<p> - Using > and 2> we can direct each output type to a particular file as in the example above. </p>

## Step 5 - HEREDOCS.

<p> - There are situations where we need to write simple scripts containing more than one line without needing to access a text editor, we can use the <b>HereDocs</b>. </p>

![Passo 14](img/Passo_14.png)

<p> - This would be an unusual way of inserting line after line into a file via append. </p>

![Passo 15](img/Passo_15.png)

<p> - Using <b>HereDocs</b> makes this much simpler and more dynamic. </p>

<p> You can type multiple lines using the <b><<</b>, followed by a keyword to determine the beginning and end of the command. We use the word EOF which comes from the early days of computing, meaning End of file. <p>

<p> - Now let's understand the functionality of this command, note that all the input from the "<<" is destined for the cat command which in turn is directed as a standard output to the texto_heredocs file. </p>

<p> - Using the cat text_heredocs command we can see that all the text has been inserted into the file via this stream. </p>
