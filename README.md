# Mobile development Programming Project
 
Η υλοποίηση της εφαρμογής που θα κάνει η εκάστοτε ομάδα θα πρέπει να ακολουθεί ένα σύνολο προδιαγραφών, έτσι ώστε να υπάρχει κοινό πεδίο αναφοράς και να είναι δικαιότερη η αξιολόγηση.

Στο πλαίσιο της εργασίας λοιπόν θα πρέπει να κατασκευάσετε μια εφαρμογή αναζήτησης πτήσεων! η εφαρμογή θα περιλαμβάνει τα απαραίτητα πεδία που πρέπει να συμπληρωθούν και καλώντας ειδικό API θα λαμβάνει και θα παρουσιάζει πληροφορίες για τις διαθέσιμες πτήσεις.

Το APi που θα καλέσετε, είναι της εταιρείας που χειρίζεται το μεγαλύτερο μέρος των συστημάτων κρατήσεων των παγκόσμιων αερομεταφορών, της Amadeus. 

_Trivia:_
Τα συστήματα κρατήσεων και οργάνωσης πτήσεων της Amadeus καλύπτουν περίπου το 50% του παγκόσμιου μεριδίου αγοράς. Η γενική κατηγορία αναφέρεται ως GDS - Global Distribution Systems και περιλαμβάνουν ένα ολοκληρωμένο πακέτο για κρατήσεις αεροπορικών θέσεων, ξενοδοχείων και ενοικίασης αυτοκινήτου. Ένα τέτοιο GDS είναι και το Amadeus. Πελάτες του Amadeus είναι τα τουριστικά πρακτορεία, ψηφιακά ή πραγματικά. Έτσι όταν κάνουμε αναζήτηση πτήσης σε μία Online σελίδα, αυτή μεταφέρει το αίτημα στην Amadeus και παίρνει από εκεί απάντηση για τη διαθεσιμότητα θέσεων και τις τιμές. Απο την απέναντι πλευρά, η κάθε αεροπορική εταιρεία, έχει συνδεθεί και αυτή στο Amadeus και έχει εισάγει τα σχέδια πτήσης, τους τύπους αεροσκαφών, τη δομή των θέσεων και την τιμή της κάθε θέσης.

Ευτυχώς για εμάς, εδώ και λίγο καιρό η Amadeus παρέχει αυτό το API ΔΩΡΕΑΝ για να το χρησιμοποιήσει οποιοσδήποτε προγραμματιστής. Αρκεί να έχει κάνει λογαριασμό στο σύστημα και να έχει πάρει apiKey. Όπως ακριβώς κάναμε και με το OpenWeatherMap api.

Η κεντρική σελίδα για να κάνετε λογαριασμό είναι https://sandbox.amadeus.com/ 

Παραδείγματα κλήσης στο api θα βρείτε εδώ https://sandbox.amadeus.com/travel-innovation-sandbox/apis/get/flights/low-fare-search

Ένα παράδειγμα με το δικό μου ApiKey με το οποίο ψάχνω πτήση απο Θεσσαλονίκη για Ντύσελντορφ στις 25 Νοεμβρίου με επιστροφή στις 28 για ένα άτομο χωρίς ενδιάμεσες στάσεις με τιμές σε νόμισμα Ευρώ με όριο τα 400 ευρώ (και το πολύ 10 αποτελέσματα):

```
https://api.sandbox.amadeus.com/v1.2/flights/low-fare-search?
apikey=YOUR_KEY
&origin=SKG
&destination=DUS
&departure_date=2016-11-25
&return_date=2016-11-28
&adults=1
&nonstop=true
&max_price=400
&currency=EUR
&number_of_results=10
```

το σύστημα της Amadeus μου απάντησε:

```
{
  "currency": "EUR",
  "results": [
    {
      "itineraries": [
        {
          "outbound": {
            "flights": [
              {
                "departs_at": "2016-11-25T10:10",
                "arrives_at": "2016-11-25T12:00",
                "origin": {
                  "airport": "SKG"
                },
                "destination": {
                  "airport": "DUS"
                },
                "marketing_airline": "A3",
                "operating_airline": "A3",
                "flight_number": "540",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "S",
                  "seats_remaining": 9
                }
              }
            ]
          },
          "inbound": {
            "flights": [
              {
                "departs_at": "2016-11-28T12:50",
                "arrives_at": "2016-11-28T16:40",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "A3",
                "operating_airline": "A3",
                "flight_number": "541",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "U",
                  "seats_remaining": 6
                }
              }
            ]
          }
        }
      ],
      "fare": {
        "total_price": "156.27",
        "price_per_adult": {
          "total_fare": "156.27",
          "tax": "48.27"
        },
        "restrictions": {
          "refundable": false,
          "change_penalties": true
        }
      }
    }
  ]
}

```

Μελετώντας το ερώτημα αλλά και τα αποτελέσματα σύντομα θα καταλάβετε ότι για να τα παρουσιάσετε σωστά πρέπει να μπορείτε να βρείτε όλους τους κωδικούς των αεροδρομίων και των αεροπορικών εταιρειών. Για παράδειγμα ο χρήστης δε θα γράψει ότι θέλέι να πετάξει στο SKG, θα γράψει: ```thessaloniki```. Θα πρέπει εσείς εσωτερικά να κάνετε τη μετατροπή απο thessaloniki σε SKG. To Amadeus έχει τη λύση και γι'αυτό, καθώς παρέχει ειδικό API αναζήτησης:

```
https://api.sandbox.amadeus.com/v1.2/airports/autocomplete?apikey=YOUR_KEY&term=thess
```

Αποτέλεσμα:

```
[
  {
    "value": "SKG",
    "label": "Thessaloníki - Thessaloniki Airport [SKG]"
  }
]
```

μπορεί να υπάρχουν και πολλαπλά αποτελέσματα:

```
https://api.sandbox.amadeus.com/v1.2/airports/autocomplete?apikey=YOUR_KEY&term=lond
```


```
[
  {
    "value": "LON",
    "label": "London [LON]"
  },
  {
    "value": "LHR",
    "label": "London Heathrow Airport [LHR]"
  },
  {
    "value": "LGW",
    "label": "London Gatwick Airport [LGW]"
  },
  {
    "value": "LTN",
    "label": "London - Luton Airport [LTN]"
  }
  .... έχει κι άλλα...
]
```

Αυτό που μας μένει τώρα είναι να αποκωδικοποιήσουμε και τον κωδικό της αεροπορικής εταιρείας. Αν προσέξατε στα αποτελέσματα πτήσεων πιο πάνω, έγραφαν:

```
"operating_airline": "A3"
```
Α3, είναι ο κωδικός ΙΑΤΑ για την 'Aegean Airlines'. Αλλά πως θα ξέρουμε την αντιστοιχία για όλες τις αεροπορικές εταιρείες; 

Σωστά μαντέψατε! Υπάρχει και γι'αυτό API !! Βρίσκεται εδώ: http://iatacodes.org/ και απαιτεί και αυτό δημιουργία λογαριασμού. 

Για να πάρουμε πληροφορίες για τον κωδικό Α3 καλούμε την εντολή:

```
https://iatacodes.org/api/v6/airlines?api_key=YOUR_KEY&code=A3
```

και παίρνουμε σαν απάντηση:

```
{
  "request": {
    "lang": "en",
    "currency": "USD",
    "time": 1,
    "id": 14776805923,
    "server": "c",
    "pid": 41988,
    "key": {
      "id": 6439,
      "api_key": ".......το κλειδί του καθενός....",
      "type": "free",
      "expired": null,
      "registered": "2016-10-28T18:25:52.000Z",
      "limits_by_hour": 2500,
      "limits_by_minute": 250,
      "usage_by_hour": 10,
      "usage_by_minute": 1
    },
    "params": {
      "code": "A3",
      "lang": "en"
    },
    "version": 6,
    "method": "airlines"
    }
  },
  "response": [
    {
      "code": "A3",
      "name": "Aegean Airlines",
      "country_code": "GR",
      "country_name": "Greece"
    }
  ]
}

```











