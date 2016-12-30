# Nota

In questa cartella l'output della conversione dal file sorgente, in formato PDF, in formato CSV.
 

```bash
# converto il PDF in CSV
java -jar tabula-0.9.1-jar-with-dependencies.jar -p 2-38 -a 122.719,40.534,801.019,561.903 -r -o output_01.csv RAP_SpA_Piano_Spazzamento_circ_1_e_8.pdf

# converto in UTF-8 il file di output che è in ISO-8859-15 
csvclean -e ISO-8859-15 output_01.csv

# aggiungo riga di intestazione
sed -i '1s/^/TIPO,VIA,TRATTI,CIRC.,FREQ.,LUN,MAR,MER,GIO,VEN,SAB,ITINERARIO,SEDE\n/' output_01_out.csv

# rimuovo le righe con celle totalmente vuote
csvgrep -c 1 -r '^.*[a-zA-Z].*$' output_01_out.csv > RAP_SpA_Piano_Spazzamento_circ_1_e_8.csv

```