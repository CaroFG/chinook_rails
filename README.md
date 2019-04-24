# README

2.2.3. Questions
Maintenant que ta BDD est prête, tu vas répondre aux questions ci-dessous :

a) Niveau facile

Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
Album.count
347

Qui est l'auteur de la chanson "White Room" ?
Track.find_by(title:"White Room").artist
Eric Clapton

Quelle chanson dure exactement 188133 milliseconds ?
Track.find_by(duration:188133).title
Perfect

Quel groupe a sorti l'album "Use Your Illusion II" 
Album.find_by(title:"Use Your Illusion II").artist
Guns N Roses

b) Niveau Moyen

Combien y a t'il d'albums dont le titre contient "Great" ? (indice)
Album.where("title like ?", "%great%").count
13


Supprime tous les albums dont le nom contient "music".
Album.where("title like ?", "%music%").destroy_all

Combien y a t'il d'albums écrits par AC/DC ?
Album.where("artist like ?", "%AC/DC%").count
2

Combien de chanson durent exactement 158589 millisecondes ?
Track.where(duration: 158589).count
0

c) Niveau Difficile

Pour ces questions, tu vas devoir effectuer des boucles dans la console Rails. C'est peu commun mais c'est faisable, tout comme dans IRB.

puts en console tous les titres de AC/DC.

Track.where(artist: "AC/DC").each do |track| puts track.title end
For Those About To Rock (We Salute You)
Put The Finger On You
Lets Get It Up
Inject The Venom
Snowballed
Evil Walks
C.O.D.
Breaking The Rules
Night Of The Long Knives
Spellbound
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie


puts en console tous les titres de l'album "Let There Be Rock".

Track.where(album: "Let There Be Rock").each do |track| puts track.title end
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie


Calcule le prix total de cet album ainsi que sa durée totale.
Track.where(album: "Let There Be Rock").each do |i| 
	puts price += i.price 
  	puts duration += i.duration
end

7.920000000000001
2453259

Calcule le coût de l'intégralité de la discographie de "Deep Purple".
2.5.1 :017 > Track.where(artist: "Deep Purple").each do |i| 
2.5.1 :018 >     puts price += i.price
2.5.1 :019?>   end

90.0899999999999

Modifie (via une boucle) tous les titres de "Iron Maiden" afin qu'ils soient affichés avec "Britney Spears" en artist.

2.5.1 :001 > Track.where(artist: "Eric Clapton").each do |i| 
2.5.1 :002 >     i.update(artist: "Britney Spears")
2.5.1 :003?>   end

