# Traitement-de-signal-TP1-
TRAITEMENT-DU-SIGNAL-TP-1
![image](https://user-images.githubusercontent.com/79712514/215353543-fab5b26b-206d-42de-a621-7c96e33fcead.png)


#Objectifs
Représentation de signaux et applications de la transformée de Fourier discrète (TFD) sous Matlab. • Evaluation de l’intérêt du passage du domaine temporel au domaine fréquentiel dans l’analyse et l’interprétation des signaux physiques réels.

L’objectif du ce TP est de voir ensemble comment se servir des outils de traitement du signal pour analyser les signaux échantillonnés. Pour cela, nous allons utiliser le logiciel MATLAB pour la simulation

Tracé des figures : toutes les figures devront être tracées avec les axes et les légendes des axes appropriés.

Travail demandé : un script Matlab commenté contenant le travail réalisé et des commentaires sur ce que vous avez compris et pas compris, ou sur ce qui vous a semblé intéressant ou pas, bref tout commentaire pertinent sur le TP.

#Représentation-temporelle-et-fréquentielle
Considérons un signal périodique x(t) constitué d’une somme de deux sinusoïdes de fréquences 15Hz et 20Hz. 𝐱(𝐭) = 𝐬𝐢𝐧(𝟐𝝅𝟏𝟓𝒕) + 𝐬𝐢𝐧(𝟐𝝅𝟐𝟎𝒕)

1- Tracer le signal x(t). Pas de temps : Te = 1/50s, Intervalle : 0, 10-Te. Pour approximer la TF continue d’un signal x(t), représenté suivant un pas Te, on utilise les deux commandes : fft et fftshif.

Te=1/50;
x=[0:Te:10-Te];
y = sin(30*pi*x) + sin(40*pi*x);
subplot(3,2,1);
plot(x,y);
title('signal x(t) :'); 
![image](https://user-images.githubusercontent.com/79712514/215353611-b69cde93-0a1f-4af7-b0e6-a6bbb1e19232.png)


On remarquera que la TF est une fonction complexe et que la fonction ainsi obtenue décrit la TF de x(t) entre –1/(2Te) et 1/(2Te) par pas de 1/(nTe) où n est le nombre de points constituant le signal x(t).

f=(0:length(x)-1)*(1/Te*length(x)); 
fy=abs(fft(y));
subplot(3,2,2); 
plot(f,fy);
title('spectre du  x(t) :'); 
![image](https://user-images.githubusercontent.com/79712514/215353625-2b8c60d9-ccf1-4b8a-8c56-acbfa650e2fe.png)


Une fois notre signal généré, calculons maintenant sa Transformée de Fourier.

fsh=[-500/2:(500/2)-1]*50/500;
fy=abs(fft(y));
subplot(3,2,3);
plot(fsh,fftshift(fy));
title('spectre du  x(t) :');
![image](https://user-images.githubusercontent.com/79712514/215353771-8b674a08-1716-4166-a49c-26fdd89f21e6.png)


Pour se rapprocher de la réalité nous allons simuler la présence d’un bruit de mesure. Pour observer le même signal que x(t), nous allons générer un bruit aléatoire Gaussien.

noise = 2*randn(size(x));
Afin de créer un signal bruité, ajoutons noise à x(t)

xnoise = x+noise; 
plot(t,xnoise,'.')
grid
title('signal x bruité');
xlabel('Temps');
ylabel('Amplitudesà');
![image](https://user-images.githubusercontent.com/79712514/215353790-948d3907-f232-4708-a89e-c499299d13bd.png)


Calculons à nouveau la Transformée de Fourier du signal bruité Sb(t)

![image](https://user-images.githubusercontent.com/79712514/215353811-250d0006-95e0-42d3-b694-5cd1ff126c14.png)

![image](https://user-images.githubusercontent.com/79712514/215353822-fa6b44a6-f736-47b2-aa70-42825374b6b7.png)


Conception du filtre pass bas idéal FILTRAGE IDEAL

![image](https://user-images.githubusercontent.com/79712514/215353872-391258d3-a778-4622-8b04-9d4e7208927f.png)


On l’applique sur le spectre de x(t)

![image](https://user-images.githubusercontent.com/79712514/215353884-04e9ec6f-1737-4e16-a9ad-24bd8c25b938.png)


![image](https://user-images.githubusercontent.com/79712514/215353899-810938be-ef80-4074-8311-06f25de8caff.png)
