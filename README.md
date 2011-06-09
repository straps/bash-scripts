# Bash utility scripts

Scripts ordered alphabetically

## pgdiff

Tables must have the same structure for pgdiff to work

    #Copy missing customers from database dbSrc to customers of dbDest database on localhost, finding missing records using the id field
    pgdiff --db dbSrc --db2 dbDest --table customers --keyfld id

    #Copy missing records from customers table of dbSrc on localhost, to dbDest on host 192.168.0.1, finding missing records using the id field
    pgdiff --db dbSrc --host2 192.168.0.1 --db2 dbDest --table customers --keyfld id

    #Copy missing records from 192.168.0.1 to localhost, database ecommerce, finding them by id
    #The --comparefld compares the prog field and if it is greater in the source database, it replaces the entire record
    pgdiff --db ecommerce --host 192.168.0.1 --host2 localhost --table orders --keyfld id --comparefld prog

Adding the `--demo` option, updates are not executed but only showed on screen; really useful to see table differences

*IMPORTANT*: --comparefld remove and reinserts founded records

*VERY IMPORTANT*: I'm not responsible for usage of the software or for any software bug

## smail
Simple `sendmail` with stdin and multiple attachment support

Usage Samples:

    #Send simple email
    smail -s 'simple email' -f from@email.com -t to@email.com -b 'email body'

    #Send HTML email
    smail -s 'html email' -f from@email.com -t to@email.com -c 'text/html' -b 'email body <b>HTML</b>'

    #Read body from file
    cat file | smail -s 'stdin email' -f from@email.com -t to@email.com

    #email with attachment
    smail -s 'see attached file' -f from@email.com -t to@email.com -a file.jpg

    #email with 2 files attached
    smail -s 'see attached files' -f from@email.com -t to@email.com -a file1.jpg -a file2.pdf

    #If an option is not know, it is appended to the subject
    smail -s 'simple email' -f from@email.com -t to@email.com -b 'email body'
    ### is the same of ###
    smail simple email -f from@email.com -t to@email.com -b 'email body'

Attachment support needs `uuencode` program; in ubuntu you can install it using `sudo apt-get install sharutils`
