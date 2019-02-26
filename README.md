# OpenSSL
Creating certificates

Download openssl from the link below

https://www.softpedia.com/dyn-postdownload.php/81a5d0f13a1b771b10067a6d4044f6f8/5c192d15/63b3/0/4

- Select the OpenSSL binaries option when going through setup process

- Create "OPEN_CONF" as a enviroment varible

- The directory of the enviroment varible should be:
```
your_directory\OpenSSL-Win64\bin\openssl.cfg
```
After this click OK to save and exit these settings.

- Open your command line and the enter:
```
genrsa -out ca.key 4096
```
- After this enter:
```
req -new -x509 -days 1826 -key ca.key -out ca.crt
```
- You will then have to answer a series of questions.

You now have a self signed certificate at this point.

Creating a certificate that will be signed by the root.

- Type in your cmd:
```
genrsa -out ia.key 4096
```
- Then enter:
```
req -new -key ia.key -out ia.csr
```
Type in the required information for these questions (Dont give the same common name for certificate)

- Make sure a password is given and a comapny name(Optional)

Type in cmd:
```
x509 -req -days 730 -in ia.csr -CA ca.crt -CAkey ca.key -set_serial 01 -out ia.crt
```
You should now have a request, key and certificate.
