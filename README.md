# MAJIQ/VOILA example

Clone this repo and then:

```bash
# Build Docker image
docker build -t majiq_voila .
# Workshop example data
wget https://majiq.biociphers.org/download/workshop_example.zip && unzip workshop_example.zip
# Fix config (samdir is now bamdirs)
cp settings.ini workshop_example/settings.ini
# majiq build
docker run -v $PWD/workshop_example:/data majiq_voila majiq build DB.gff3 -c settings.ini -o out
# majiq psi
docker run -v $PWD/workshop_example:/data majiq_voila majiq psi -o out -n test out/workshop_Adr1.majiq out/workshop_Adr2.majiq out/workshop_Adr3.majiq out/workshop_Cer1.majiq out/workshop_Cer2.majiq
# voila view
docker run -v $PWD/workshop_example:/data -p 3000:3000 majiq_voila voila view -p 3000 --host 0.0.0.0 out
# => browse to http://localhost:3000 with web browser to see voila
```
