# CDOC · [![Build Status](https://travis-ci.org/martinpaljak/cdoc.svg?branch=master)](https://travis-ci.org/martinpaljak/cdoc) [![Coverity status](https://scan.coverity.com/projects/martinpaljak-cdoc/badge.svg?flat=1)](https://scan.coverity.com/projects/martinpaljak-cdoc)  [![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.github.martinpaljak/cdoc/badge.svg)](https://mvnrepository.com/artifact/com.github.martinpaljak/cdoc) [![Javadocs](https://www.javadoc.io/badge/com.github.martinpaljak/cdoc.svg)](https://www.javadoc.io/doc/com.github.martinpaljak/cdoc) [![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/martinpaljak/cdoc/blob/master/LICENSE)

Small Java library for _creating_ encrypted CDOC files, with Elliptic Curve support ("CDOC 1.1 amendment").

- Include dependency
```xml
<dependency>
    <groupId>com.github.martinpaljak</groupId>
    <artifactId>cdoc</artifactId>
    <version>0.0.2</version>
</dependency>
```
- Write code, with the help of [javadoc](https://www.javadoc.io/doc/com.github.martinpaljak/cdoc)
```java
import org.esteid.cdoc.CDOC;

// 1. Where to write the output
File output = File.createTempFile("foobar", null);

// 2. Which files to encrypt
List<File> files = new ArrayList<>();
files.add(new File("/some/file"));
files.add(new File("/some/other/file"));

// 3. To whom to encrypt
List<X509Certificate> recipients = new ArrayList<>();
recipients.add();

// 4. Encrypt.
CDOC.encrypt(output, files, recipients);

// 5. output is now an encrypted file
```

### Supported formats:
- [CDOC 1.0](https://github.com/martinpaljak/idcrypt/wiki/CDOC-1.0): AES-128 CBC, *RSA recipients only*, XML base64 container (supported by [@open-eid](https://github.com/open-eid) software)
- **[CDOC 1.1](https://github.com/martinpaljak/cdoc/blob/master/src/test/resources/CDOC-A-101-7.pdf) (default):** AES-256 GCM, RSA and ECC recipients, XML base64 container (supported _soon_ by [@open-eid](https://github.com/open-eid) software)
- [CDOC 2.0](FORMAT.md): AES-256 GCM, RSA and ECC recipients, ZIP container (_at least_ 30%, usually 50% smaller files compared to XML, not (yet) supported by @open-eid software) 
