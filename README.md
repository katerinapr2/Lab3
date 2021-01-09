# Lab3 
## Αρχιτεκτονική Υπολογιστών
### Εργαστηριακή Άσκηση 2
#### Παπαδόπουλος Γρηγόρης - 9441
#### Πρόκου Κατερίνα - 9476
#### ~~~ Αναλυτική Αναφορά ~~~   
***Βήμα 1ο***  
***_1._***   ***Dynamic Power***  
Η δυναμική κατανάλωση ενέργειας προέρχεται από τη δραστηριότητα των λογικών πυλών εντός ενός επεξεργαστή. Όταν οι λογικές πύλες εναλλάσσονται, ρέει ενέργεια καθώς οι πυκνωτές μέσα τους φορτίζονται και αποφορτίζονται. Η δυναμική ισχύς που καταναλώνεται από μια CPU είναι περίπου ανάλογη της συχνότητας της CPU και του τετραγώνου της τάσης της:
~~~
Dynamic_power = A * C * V^2 * f   
~~~
όπου A είναι ο Activity factor, C είναι η μεταβαλλόμενη χωρητικότητα φορτίου, το f είναι η συχνότητα και το V είναι η τάση του επεξεργαστή.   

***Leakage power***  
Η κατανάλωση ισχύος λόγω διαρροής προέρχεται από το μικρο-επίπεδο στα τρανζίστορ. Μικρές ποσότητες ρευμάτων ρέουν πάντα μεταξύ των διαφορετικών τμημάτων του τρανζίστορ. Το μέγεθος αυτών των ρευμάτων εξαρτάται από την κατάσταση του τρανζίστορ, τις διαστάσεις του, τις φυσικές ιδιότητες και μερικές φορές τη θερμοκρασία. Η συνολική ποσότητα ρεύματος διαρροής τείνει να διογκώνεται για αύξηση της θερμοκρασίας και μείωση των μεγεθών τρανζίστορ. 
~~~
Leakage_power = f(Vdd, Vth, W/L) = (Voltage^2) / Constant(Vth, W/L)    
~~~ 
Καταλαβαίνουμε, λοιπόν, πως η δυναμική εξαρτάται από τη συχνότητα του ρολογιού, ενώ το ρεύμα διαρροής από την τάση τροφοδοσίας της CPU.   

_Όταν τρέξω δύο διαφορετικά προγράμματα_ σε έναν επεξεργαστή θα αλλάξει το Dynamic Power αλλά και το Dynamic Runtime, καθώς αυτό ορίζεται ως το πηλίκο _dynamic power / simulation time_ και λόγω των διαφορετικών εντολών που περιέχουν τα δύο προγράμματα θα υπήρχαν οι εξής αλλαγές :
* του Activity Switch, γιατί διαφορετικές αλλαγές προκαλλούν διαφορετική δραστηριότητα των transistor, γεγονός που προκαλεί την αλλαγή του Dynamic Power.  
* του Simulation Time, γιατί αλλάζει τόσο ο συνολικός αριθμός των εντολών όσο και ο τύπος των εντολών που καθορίζουν τον συνολικό χρόνο, η οποία αθροιστικά με την προηγούμενη επιφέρει αλλαγή στο Dynamic Runtime.  
 
Από την άλλη μεριά, το Leakage Power παραμένει σταθερό καθώς οφείλεται σε σταθερά ρεύματα τα οποία δεν αλλάζουν με την δραστηριότητα του transistor συνεπώς και με την εκτέλεση διαφορετικών προγραμμάτων.   
 
**2.** Η _χωρητικότητα_ της μπαταρίας μετριέται σε _μονάδες ρεύματος * μονάδες χρόνου_ και η _ισχύς_ των επεξεργαστών αποτελούν ενέργεια ανά μονάδα χρόνου.Έπειτα απο αντικαταστάσεις είναι εύκολο να διακρίνουμε οτι η ζωή της μπαταρίας καταναλώνεται με ρυθμό 10 φορές μεγαλύτερο για τον ενεργοβόρο επεξεργαστή.
Έτσι μπορούμε να συμπεράνουμε οτι δεν υπάρχει περίπτωση να παίρνουμε μεγαλύτερη διάρκεια μπαταρίας.Ωστόσο λόγω της αυξημένης ισχύος του θα μπορούσαμε να εκτελούμε προγράμματα σε ταχύτερο ρυθμό και στο σημείο που αυτός θα γινόταν ίσος τότε θα μπορούσαμε να ισχυριστούμε οτι ο ενεργοβόρος επεξεργαστής 
δίνει ισάξια ζωή μπαταρίας.Το mcpat δεν παρέχει κάποιο στατιστικό που να αναφέρεται στο ρυθμό επεξεργασίας των δεδομένων, οπότε δεν μπορούμε να βγάλουμε κάποιο συμπέρασμα.  
Τα παραπάνω αποτελέσματα προκύπτουν από τις παρακάτω σχέσεις:  
~~~
Battery_Life_1 = I1 * t1   
Battery_Life_2 = I2 * t2  
και   
P1 = V * I1    
P2 = V * I2  
~~~   
όπου P1 = 4W και P2 = 40W.  
 
***3.***  ***Xeon.xml***   

    *****************************************************************************************
    Technology 65 nm
    Using Long Channel Devices When Appropriate
    Interconnect metal projection= aggressive interconnect technology projection
    Core clock Rate(MHz) 3400
    *****************************************************************************************
    Processor:
      Area = 410.507 mm^2
      Peak Power = 134.938 W
      Total Leakage = 36.8319 W
      Peak Dynamic = 98.1063 W
      Subthreshold Leakage = 35.1632 W
      Subthreshold Leakage with power gating = 16.3977 W
      Gate Leakage = 1.66871 W
      Runtime Dynamic = 72.9199 W

    Total Cores: 2 cores 
    Device Type= ITRS high performance device type
      Area = 111.713 mm^2
      Peak Dynamic = 78.5978 W
      Subthreshold Leakage = 24.1131 W
      Subthreshold Leakage with power gating = 10.3006 W
      Gate Leakage = 1.49026 W
      Runtime Dynamic = 55.7891 W

    Total L3s: 
    Device Type= ITRS high performance device type
      Area = 293.281 mm^2
      Peak Dynamic = 6.70159 W
      Subthreshold Leakage = 10.9824 W
      Subthreshold Leakage with power gating = 6.06659 W
      Gate Leakage = 0.165767 W
      Runtime Dynamic = 4.32382 W

    Total NoCs (Network/Bus): 
    Device Type= ITRS high performance device type
      Area = 5.51364 mm^2
      Peak Dynamic = 12.807 W
      Subthreshold Leakage = 0.0678232 W
      Subthreshold Leakage with power gating = 0.0305204 W
      Gate Leakage = 0.0126787 W
      Runtime Dynamic = 12.807 W

    *****************************************************************************************

 ***ARM_A9_2GHz.xml***  
 
    *****************************************************************************************
    Technology 40 nm
    Using Long Channel Devices When Appropriate
    Interconnect metal projection= conservative interconnect technology projection
    Core clock Rate(MHz) 2000

    *****************************************************************************************
    Processor:
      Area = 5.39698 mm^2
      Peak Power = 1.74189 W
      Total Leakage = 0.108687 W
      Peak Dynamic = 1.6332 W
      Subthreshold Leakage = 0.0523094 W
      Gate Leakage = 0.0563774 W
      Runtime Dynamic = 2.96053 W

    Total Cores: 2 cores 
    Device Type= ITRS low operating power device type
      Area = 4.84735 mm^2
      Peak Dynamic = 1.57159 W
      Subthreshold Leakage = 0.0484486 W
      Gate Leakage = 0.0501375 W
      Runtime Dynamic = 1.06575 W

    Total First Level Directory: 
    Device Type= ITRS low operating power device type
      Area = 0.535391 mm^2
      Peak Dynamic = 0.045212 W
      Subthreshold Leakage = 0.00370577 W
      Gate Leakage = 0.0060234 W
      Runtime Dynamic = 1.81276 W

    Total NoCs (Network/Bus): 
    Device Type= ITRS low operating power device type
      Area = 0.014239 mm^2
      Peak Dynamic = 0.0164048 W
      Subthreshold Leakage = 0.000155022 W
      Gate Leakage = 0.000216526 W
      Runtime Dynamic = 0.0820239 W

    *****************************************************************************************

Ως energy efficiency ορίζεται το πηλίκο των συνολικών εντολών που εκτελούνται στον χρόνο προς την ισχύ που χρειάζεται ο επεξεργαστής για να τις εκτελέσει.Οπότε ορίζεται από τον τύπο:  
~~~
Energy_eff = instruction_rate / (Runtime Dynamic + Leakage Power)     
~~~
Για τον Arm έστω a το instruction_rate, οπότε για τον Xeon το instruction_rate b=40*a. 
~~~
ARM : Energy_eff = a / (2.96053 + 0.108687) = 9.54 * a   
Χeon : Energy_eff = b / (72.9199 + 36.8319) = 40 * a / 109.75 = 0.36 * a    
~~~
Άρα παρατηρούμε ότι ο ARM είναι 26,5 φορές πιο αποδοτικός ενεργειακά για το δεδομένο πρόγραμμα.   

***Βήμα 2ο***   
**1.**  
Καταναλώσεις ενέργειας:  
Για το **_bzip_**:  
* cacheline_16 --> energy is 78.839680 mJ      
* cacheline 512 --> energy is 961.776440 mJ  
* cacheline 1024 --> energy is 3443.029590 mJ  

* l1dcache_associativity_1 --> energy is 124.996337 mJ
* l1dcache_associativity_4 --> energy is 100.334350 mJ
* l1dcache_associativity_8 --> energy is 108.405443 mJ
* l1dcache_associativity_16 --> energy is 131.777040 mJ
* l1dcache_associativity_32 --> energy is 168.259472 mJ
* l1dcache_associativity_64 --> energy is 280.650614 mJ

* l1dcachesize_16kB --> energy is 75.211444 mJ
* l1dcachesize_32kB --> energy is 74.298779 mJ
* l1dcachesize_128kB --> energy is 153.069087 mJ  

* l1icache_associativity_1 --> energy is 130.580376 mJ  
* l1icache_associativity_2 --> energy is 134.292457 mJ 
* l1icache_associativity_16 --> energy is 139.939999 mJ
* l1icache_associativity_256 --> energy is 123.935577 mJ  
 
* l1icache_size_16 --> energy is 123.362208 mJ  
* l1icache_size_64 --> energy is 157.831262 mJ 
* l1icache_size_128 --> energy is 181.737013 mJ  

* l2cache_associativity_1 --> energy is 125.096851 mJ
* l2cache_associativity_16 --> energy is 124.009691 mJ
* l2cache_associativity_64 --> energy is 125.596278 mJ 
* l2cache_associativity_256 --> energy is 124.267460 mJ

* l2cache_size_512 --> energy is 127.961542 mJ
* l2cache_size_1MB --> energy is 125.217515 mJ
* l2cache_size_4MB --> energy is 123.157072 mJ    

![image](https://user-images.githubusercontent.com/58628111/102759601-02178180-437d-11eb-96c5-7022918fdf98.png)   
![image](https://user-images.githubusercontent.com/58628111/102759616-0479db80-437d-11eb-8b24-a98b5229ff72.png) ![image](https://user-images.githubusercontent.com/58628111/102759623-0774cc00-437d-11eb-842d-3cc66ecc2fff.png)   
![image](https://user-images.githubusercontent.com/58628111/102759628-09d72600-437d-11eb-827d-7b0ad8d56301.png) ![image](https://user-images.githubusercontent.com/58628111/102759646-0cd21680-437d-11eb-98fb-f3460d51621d.png)   
![image](https://user-images.githubusercontent.com/58628111/102759653-0fcd0700-437d-11eb-92a4-1a41727eaef5.png) ![image](https://user-images.githubusercontent.com/58628111/102759658-13608e00-437d-11eb-9eff-b75909ca5f24.png)   


***********************************************************

Για το **_hmmer_**:  
* cacheline_64 --> energy is 0.057471 mJ    
* cacheline 128 --> energy is 0.051322 mJ   
* cacheline 256 --> energy is 0.091543 mJ    
* cacheline 512 --> energy is 0.261710 mJ   
* cacheline 1024 --> energy is 0.946994 mJ  

* l1dcache_associativity_1 --> energy is 0.057364 mJ
* l1dcache_associativity_2 --> energy is 0.057471 mJ
* l1dcache_associativity_4 --> energy is 0.044596 mJ
* l1dcache_associativity_8 --> energy is 0.046220 mJ
* l1dcache_associativity_16 --> energy is 0.050639 mJ
* l1dcache_associativity_32 --> energy is 0.057868 mJ
* l1dcache_associativity_64 --> energy is 0.078206 mJ  

* l1dcachesize_8kB --> energy is 0.037536 mJ
* l1dcachesize_16kB --> energy is 0.036855 mJ
* l1dcachesize_32kB --> energy is 0.057471 mJ
* l1dcachesize_64kB --> energy is 0.057471 mJ
* l1dcachesize_128kB --> energy is 0.071391 mJ  

* l1icache_associativity_1 --> energy is 0.058735 mJ  
* l1icache_associativity_2 --> energy is 0.057471 mJ  
* l1icache_associativity_4 --> energy is 0.061293 mJ  
* l1icache_associativity_8 --> energy is 0.063433 mJ
* l1icache_associativity_16 --> energy is 0.066746 mJ
* l1icache_associativity_32 --> energy is 0.071833 mJ  

* l1icache_size_8 --> energy is 0.058416 mJ  
* l1icache_size_16 --> energy is 0.058435 mJ  
* l1icache_size_32 --> energy is 0.057471 mJ 
* l1icache_size_64 --> energy is 0.057471 mJ 
* l1icache_size_128 --> energy is 0.090065 mJ  

* l2cache_associativity_1 --> energy is 0.057464 mJ
* l2cache_associativity_2 --> energy is 0.057468 mJ
* l2cache_associativity_4 --> energy is 0.057469 mJ
* l2cache_associativity_8 --> energy is 0.057471 mJ
* l2cache_associativity_16 --> energy is 0.057485 mJ
* l2cache_associativity_32 --> energy is 0.057485 mJ
* l2cache_associativity_64 --> energy is 0.057551 mJ  

* l2cache_size_512 --> energy is 0.057244 mJ
* l2cache_size_1MB --> energy is 0.057337 mJ
* l2cache_size_2MB --> energy is 0.057471 mJ
* l2cache_size_4MB --> energy is 0.057743 mJ   

![image](https://user-images.githubusercontent.com/58628111/102758161-017deb80-437b-11eb-8439-fb879b4a8828.png)   
![image](https://user-images.githubusercontent.com/58628111/102758172-0478dc00-437b-11eb-8afb-f5f91f2b59d9.png) ![image](https://user-images.githubusercontent.com/58628111/102758179-080c6300-437b-11eb-926a-8059071f3713.png)   
![image](https://user-images.githubusercontent.com/58628111/102758192-0b075380-437b-11eb-9ced-4c20c988aa4a.png) ![image](https://user-images.githubusercontent.com/58628111/102758200-0e9ada80-437b-11eb-8939-bc0bb33c5440.png)   
![image](https://user-images.githubusercontent.com/58628111/102758207-1195cb00-437b-11eb-8b0c-10063b6a2b5d.png) ![image](https://user-images.githubusercontent.com/58628111/102758220-1490bb80-437b-11eb-9aab-97478a831730.png)   


**********************************************************

Για το **_libm_**:  
* cacheline_64 --> energy is 232.761059 mJ
* cacheline 128 --> energy is 210.373858 mJ   
* cacheline 256 --> energy is 334.932056 mJ 
* cacheline 512 --> energy is 904.768681 mJ   
* cacheline 1024 --> energy is 2881.449984 mJ  

* l1dcache_associativity_1 --> energy is 233.477155 mJ
* l1dcache_associativity_2 --> energy is 232.761059 mJ
* l1dcache_associativity_4 --> energy is 184.889790 mJ
* l1dcache_associativity_8 --> energy is 196.386753 mJ
* l1dcache_associativity_16 --> energy is 226.053216 mJ
* l1dcache_associativity_32 --> energy is 272.618187 mJ
* l1dcache_associativity_64 --> energy is 413.460174 mJ   

* l1dcachesize_16kB --> energy is 143.163734 mJ
* l1dcachesize_32kB --> energy is 144.615867 mJ
* l1dcachesize_64kB --> energy is 232.761059 mJ
* l1dcachesize_128kB --> energy is 290.364897 mJ  

* l1icache_associativity_1 --> energy is 233.138032 mJ 
* l1icache_associativity_2 --> energy is 232.761059 mJ  
* l1icache_associativity_4 --> energy is 246.585985 mJ  
* l1icache_associativity_8 --> energy is 254.310288 mJ
* l1icache_associativity_16 --> energy is 266.108376 mJ
* l1icache_associativity_32 --> energy is 283.738312 mJ 

* l1icache_size_16 --> energy is 231.488843 mJ  
* l1icache_size_32 --> energy is 232.761059 mJ 
* l1icache_size_64 --> energy is 303.494180 mJ 
* l1icache_size_128 --> energy is 353.408560 mJ  

* l2cache_associativity_1 --> energy is 232.685030 mJ
* l2cache_associativity_2 --> energy is 232.725929 mJ
* l2cache_associativity_4 --> energy is 232.732920 mJ
* l2cache_associativity_8 --> energy is 232.761059 mJ
* l2cache_associativity_16 --> energy is 232.818562 mJ
* l2cache_associativity_32 --> energy is 232.958909 mJ
* l2cache_associativity_64 --> energy is 233.805240 mJ  

* l2cache_size_1MB --> energy is 232.534142 mJ
* l2cache_size_2MB --> energy is 232.761059 mJ
* l2cache_size_4MB --> energy is 234.274592 mJ    

![image](https://user-images.githubusercontent.com/58628111/102759303-99c8a000-437c-11eb-8924-cf0007d21fa1.png)  
![image](https://user-images.githubusercontent.com/58628111/102759315-9d5c2700-437c-11eb-8084-f193b202c2da.png) ![image](https://user-images.githubusercontent.com/58628111/102759324-a0571780-437c-11eb-962c-e3e197cee283.png)   
![image](https://user-images.githubusercontent.com/58628111/102759348-a947e900-437c-11eb-9353-6a4525316215.png) ![image](https://user-images.githubusercontent.com/58628111/102759356-ac42d980-437c-11eb-9370-2514137262ca.png)   
![image](https://user-images.githubusercontent.com/58628111/102759363-af3dca00-437c-11eb-95d2-ab744c17de25.png) ![image](https://user-images.githubusercontent.com/58628111/102759373-b238ba80-437c-11eb-867d-02067c77a5c5.png)   


*************************************************************  

Για το **_sjeng_**:  
* cacheline_16 --> energy is 1177.384897 mJ
* cacheline 256 --> energy is 837.079030 mJ 

* l1dcache_associativity_1 --> energy is 657.900532 mJ
* l1dcache_associativity_16 --> energy is 635.302559 mJ
* l1dcache_associativity_64 --> energy is 1087.340624 mJ   

* l1dcachesize_16kB --> energy is 413.513086 mJ
* l1dcachesize_32kB --> energy is 417.469931 mJ
* l1dcachesize_128kB --> energy is 821.812740 mJ

* l1icache_associativity_1 --> energy is 659.135504 mJ 
* l1icache_associativity_16 --> energy is 757.266740 mJ  

* l1icache_size_16 --> energy is 655.449414 mJ  
* l1icache_size_64 --> energy is 867.200808 mJ 
* l1icache_size_128 --> energy is 1013.955760 mJ 

* l2cache_associativity_1 --> energy is 658.792473 mJ
* l2cache_associativity_2 --> energy is 659.145349 mJ
* l2cache_associativity_16 --> energy is 659.377459 mJ
* l2cache_associativity_512 --> energy is 698.588206 mJ 

* l2cache_size_512 --> energy is 654.961541 mJ
* l2cache_size_1MB --> energy is 656.784217 mJ
* l2cache_size_4MB --> energy is 663.003266 mJ  

![image](https://user-images.githubusercontent.com/58628111/102760052-a3063c80-437d-11eb-9c89-c9e01b824a1d.png)   
![image](https://user-images.githubusercontent.com/58628111/102760063-a6012d00-437d-11eb-93d7-01bd22bd9047.png) ![image](https://user-images.githubusercontent.com/58628111/102760072-a8638700-437d-11eb-8086-15bfd30e85b4.png)   
![image](https://user-images.githubusercontent.com/58628111/102760112-b6b1a300-437d-11eb-95e2-d2306ea34b83.png) ![image](https://user-images.githubusercontent.com/58628111/102760119-b9ac9380-437d-11eb-9658-c526230e69f3.png)   
![image](https://user-images.githubusercontent.com/58628111/102760127-bc0eed80-437d-11eb-9300-1f2b11d05349.png) ![image](https://user-images.githubusercontent.com/58628111/102760200-d8128f00-437d-11eb-8956-044841e7da23.png)   


Φαίνεται πως τα παραπάνω αποτελέσματα προκύπτουν από _(leakage + dynamic) * runtime_.  

Τα πιθανά σφάλματα που προκύπτουν στην παραπάνω ανάλυση οφείλονται σε διάφορους παράγοντες.Αρχικά πρέπει να λάβουμε υπόψιν ότι κάθε simulator, όπως ο gem5 αλλά και ο mcpat δεν μπορούν να προβλέψουν τα πιθανά σφάλματα που προκύπτουν κατά την εκτέλεση τους, τα οποία αθροίζονται μαζί με αυτά που προβλέπονται από τους simulators, γεγονός που δημιουργεί ψευδή εικόνα για το εικονικό σύστημα.Λάθη ακόμα προκύπτουν και από τις πιθανές στρογγυλοποιήσεις που συμβαίνουν κατά την εκτέλεση.Το γεγονός ότι χρησιμοποιούμε δύο διαφορετικούς simulator για την ανάλυση διαφορετικών πτυχών του συστήματος επιφέρει αυξημένο αριθμό λαθών στην ανάλυση καθώς για κάθε λάθος που προκύπτει σε ένα στάδιο (π.χ gem5) αυτό θα πολλαπλασιαστεί στα επόμενα (π.χ mcpat).Γενικά μπορούμε να συμπεράνουμε ότι όσο περισσότερα στάδια εικονικής ανάλυσης προσθέτουμε (simulations) τα αποτελέσματα θα απομακρύνονται από αυτά που θα προέκυπταν από την απευθείας ανάλυση του πραγματικού συστήματος.   

**Κριτική**  
Η συγκεκριμένη εργαστηριακή άσκηση, σαν συνέχεια των προηγούμενων, έδινε μια ολοκληρωμένη εικόνα για την προσωμοίωση συστημάτων και την μελέτη τους.  

#### Πηγές   
https://en.wikipedia.org/wiki/Processor_power_dissipation#cite_note-ActivityFactor-11   
https://asic-soc.blogspot.com/   
https://www.sciencedirect.com/   
https://anysilicon.com/




