mkdir practica1
mkdir practica2
cd practica1
sudo gedit Readme.txt
ls -l
cp ~/Documents/practica1/Readme.txt ~/Documents/practica2/
cd ~/Documents/practica2
mkdir vacia
mkdir info
sudo gedit ~/Documents/practica2/info/Readme.txt
cp -r ~/Documents/practica2/vacia ~/Documents/practica1/
cp -r ~/Documents/practica2/info ~/Documents/practica1/
rm ~/Documents/practica1/Readme.txt
rm -r ~/Documents/practica1/info
