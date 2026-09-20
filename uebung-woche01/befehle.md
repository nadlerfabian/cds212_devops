# 1. Aktuelles Arbeitsverzeichnis anzeigen
pwd

# 2. Ins Home-Verzeichnis wechseln, ohne vollständigen Pfad
cd ~

# alternativ einfach:
cd


# 3. Verzeichnis uebung-ha anlegen
mkdir uebung-ha

# 4. Leere Datei liste.txt darin anlegen
touch uebung-ha/liste.txt

# 5. Inhalt ausführlich inkl. versteckter Dateien anzeigen
ls -la uebung-ha

# 6. "Hallo DevOps" in liste.txt schreiben (überschreibt bisherigen Inhalt)
echo "Hallo DevOps" > uebung-ha/liste.txt

# 7. Zweite Zeile anhängen
echo "Zweite Zeile" >> uebung-ha/liste.txt

# 8. Gesamten Dateiinhalt ausgeben
cat uebung-ha/liste.txt

# 9. Datei kopieren
cp uebung-ha/liste.txt uebung-ha/liste-backup.txt

# 10. Backup umbenennen
mv uebung-ha/liste-backup.txt uebung-ha/sicherung.txt

# 11. Anzahl Zeilen zählen
wc -l uebung-ha/liste.txt

# 12. In /etc nur auf oberster Ebene nach *.conf suchen,
# Fehlermeldungen unterdrücken
find /etc -maxdepth 1 -type f -name "*.conf" 2>/dev/null

# 13. Eigenen Benutzer in /etc/passwd suchen
grep "^$USER:" /etc/passwd

# 14. Erste fünf Zeilen anzeigen
head -n 5 /etc/passwd

# 15. Letzte drei Zeilen anzeigen
tail -n 3 /etc/passwd

# 16. Manpage zu chmod öffnen
man chmod
# Zum Schliessen danach:
q

# 17. Nur Besitzer darf lesen und schreiben
chmod 600 uebung-ha/sicherung.txt

# 18. Skript erstellen
echo 'echo "Hallo"' > uebung-ha/hallo.sh

# ausführbar machen
chmod +x uebung-ha/hallo.sh

# ausführen
./uebung-ha/hallo.sh

# 19. Rechte symbolisch anzeigen
ls -l uebung-ha/sicherung.txt

# ergibt z.B.:
# -rw------- 1 user user ... sicherung.txt

# 20. Mit zwei Befehlen + Pipe Anzahl Zeilen von /etc/passwd zählen
cat /etc/passwd | wc -l