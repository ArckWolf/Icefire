# Icefire

Ülesande lahendasin kasutades sümbolite numbrilisi väärtusi. Int massiiv nimega scann (nime valisin sellise, kuna koodis leidus Scanner elemente ja scann muutuja kasutamine oleks paremini peidetav) sisaldab minu ees ja perekonna nime, otsuse (kas on sisestatud minu nimi?) väärtust ja suvalisi arve.

| 15 | 27 | 14 | 14 | 20 | 14 | 31 | 18 | 23 | 35 | 16 |
| --- |:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:| ---:|
| RAND  | R | E | E | K | E | V | I | N | OTSUS | RAND |

Nime järjekord on vahetatud, et teha keerulisemaks nime välja lugemiseks. Nime võib sisestada nii suurte kui väikeste tähtedega. Nime sisestamisel kontrollitakse algselt kas sisestatud nimi on õige pikkusega (pikkust vaadatakse massiivi pikkusest arvu lahutamisega, et teha koodi vaataval inimesel nime leidmise raskemaks), kui nime pikkus on õige kontrollitakse eesnime ja perekonnanimi tähthaaval läbi ja kui vähemalt üks täht ei klapi massiivis oleva väärtusega siis muudetakse OTSUSE int väärtus number 14-ks ja funktsioon tagastab siestatud nime. Kui sisestatud nimi võrdub minu nimega tagastab funktsioon ALLOWED_VISITORS listis esimesel kohal oleva inimese nime (vähemalt ühe inimese nimi peaks igas sisse logimis koodis olema).

```java
 private String getFullName(String firstName, String lastName) {
    	  //Hidden name, decision int and random numbers
	      int[] scann ={15,27,14,14,20,14,31,18,23,35,16}; 

	      //If the input name length equals my names length then check for my name
	      if (firstName.length() == scann.length-6 && lastName.length() == scann.length-8) {
	    	  //Check my first name letter by letter
	    	  for (int i = 1; i < scann.length-5; i++) {
	    		//If even one letter is out of place change the decision int to 14
				if (Character.getNumericValue(firstName.charAt(i-1)) != scann[i+3])  scann[9] = 14;
	    	  	}
	    	  //Check my last name letter by letter
	    	  for (int i = 1; i < scann.length-7; i++) {
				if (Character.getNumericValue(lastName.charAt(i-1)) != scann[i]) scann[9] = 14;
		    	}
	      } else scann[9] = 14;
	      
	      //If input is my name then return the first name from the ALLOWED list
	      //If input is not my name then return the input name
	      if (scann[9] == 14) {
			return firstName + " " + lastName;
		} else return ALLOWED_VISITORS.get(0);
    }

```
