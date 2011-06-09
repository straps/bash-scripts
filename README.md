# Bash utility scripts

## pgdiff

## smail
Simple sendmail with stdin and multiple attachment support

Usage Samples:

  #Send simple email
  smail -s 'simple email' -f from@email.com -t to@email.com -b 'email body'

  #Send HTML email
  smail -s 'html email' -f from@email.com -t to@email.com -c 'text/html' -b 'email body <b>HTML</b>'

  #Read body from file
  cat file | smail -s 'html email' -f from@email.com -t to@email.com

  #email with attachment
  smail -s 'html email' -f from@email.com -t to@email.com -a file.jpg

  #email with 2 files attached
  smail -s 'html email' -f from@email.com -t to@email.com -a file1.jpg -a file2.pdf

  #If an option is not know, it is appended to the subject
  smail -s 'simple email' -f from@email.com -t to@email.com -b 'email body'
  ### is the same of ###
  smail simple email -f from@email.com -t to@email.com -b 'email body'

