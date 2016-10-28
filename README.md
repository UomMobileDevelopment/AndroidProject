# Mobile development Programming Project
 
Η υλοποίηση της εφαρμογής που θα κάνει η εκάστοτε ομάδα θα πρέπει να ακολουθεί ένα σύνολο προδιαγραφών, έτσι ώστε να υπάρχει κοινό πεδίο αναφοράς και να είναι δικαιότερη η αξιολόγηση.

Στο πλαίσιο της εργασίας λοιπόν θα πρέπει να κατασκευάσετε μια εφαρμογή αναζήτησης πτήσεων! η εφαρμογή θα περιλαμβάνει τα απαραίτητα πεδία που πρέπει να συμπληρωθούν και καλώντας ειδικό API θα λαμβάνει και θα παρουσιάζει πληροφορίες για τις διαθέσιμες πτήσεις.

Το APi που θα καλέσετε, είναι της εταιρείας που χειρίζεται το μεγαλύτερο μέρος των συστημάτων κρατήσεων των παγκόσμιων αερομεταφορών, της Amadeus. 
_Trivia:_
Τα συστήματα κρατήσεων και οργάνωσης πτήσεων της Amadeus καλύπτουν περίπου το 50% του παγκόσμιου μεριδίου αγοράς. Η γενική κατηγορία αναφέρεται ως GDS - Global Distribution Systems και περιλαμβάνουν ένα ολοκληρωμένο πακέτο για κρατήσεις αεροπορικών θέσεων, ξενοδοχείων και ενοικίασης αυτοκινήτου. Ένα τέτοιο GDS είναι και το Amadeus. Πελάτες του Amadeus είναι τα τουριστικά πρακτορεία, ψηφιακά ή πραγματικά. Έτσι όταν κάνουμε αναζήτηση πτήσης σε μία Online σελίδα, αυτή μεταφέρει το αίτημα στην Amadeus και παίρνει από εκεί απάντηση για τη διαθεσιμότητα θέσεων και τις τιμές. Απο την απέναντι πλευρά, η κάθε αεροπορική εταιρεία, έχει συνδεθεί και αυτή στο Amadeus και έχει εισάγει τα σχέδια πτήσης, τους τύπους αεροσκαφών, τη δομή των θέσεων και την τιμή της κάθε θέσης.

Ευτυχώς για εμάς, εδώ και λίγο καιρό η Amadeus παρέχει αυτό το API ΔΩΡΕΑΝ για να το χρησιμοποιήσει οποιοσδήποτε προγραμματιστής. Αρκεί να έχει κάνει λογαριασμό στο σύστημα και να έχει πάρει apiKey. Όπως ακριβώς κάναμε και με το OpenWeatherMap api.

Η κεντρική σελίδα για να κάνετε λογαριασμό είναι https://sandbox.amadeus.com/ 

Παραδείγματα κλήσης στο api θα βρείτε εδώ https://sandbox.amadeus.com/travel-innovation-sandbox/apis/get/flights/low-fare-search

Ένα παράδειγμα με το δικό μου ApiKey με το οποίο ψάχνω πτήση απο Θεσσαλονίκη για Ντύσελντορφ στις 25 Νοεμβρίου με επιστροφή στις 28 για ένα άτομο χωρίς ενδιάμεσες στάσεις με τιμές σε νόμισμα Ευρώ (θέλω το πολύ 10 αποτελέσματα):

```
https://api.sandbox.amadeus.com/v1.2/flights/low-fare-search?apikey=ZDc00QOByB4h87Lp96mXyJyxHP29OjqZ&origin=SKG&destination=DUS&departure_date=2016-11-25&return_date=2016-11-28&adults=1&nonstop=true&max_price=400&currency=EUR&number_of_results=10
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
    },
    {
      "itineraries": [
        {
          "outbound": {
            "flights": [
              {
                "departs_at": "2016-11-25T16:00",
                "arrives_at": "2016-11-25T16:55",
                "origin": {
                  "airport": "SKG"
                },
                "destination": {
                  "airport": "VIE"
                },
                "marketing_airline": "LH",
                "operating_airline": "OS",
                "flight_number": "6441",
                "aircraft": "E95",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T17:35",
                "arrives_at": "2016-11-25T19:15",
                "origin": {
                  "airport": "VIE"
                },
                "destination": {
                  "airport": "DUS"
                },
                "marketing_airline": "LH",
                "operating_airline": "OS",
                "flight_number": "6355",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 9
                }
              }
            ]
          },
          "inbound": {
            "flights": [
              {
                "departs_at": "2016-11-28T10:10",
                "arrives_at": "2016-11-28T11:50",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "VIE"
                },
                "marketing_airline": "OS",
                "operating_airline": "OS",
                "flight_number": "152",
                "aircraft": "321",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "K",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-28T12:35",
                "arrives_at": "2016-11-28T15:20",
                "origin": {
                  "airport": "VIE"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "OS",
                "operating_airline": "OS",
                "flight_number": "809",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "K",
                  "seats_remaining": 9
                }
              }
            ]
          }
        }
      ],
      "fare": {
        "total_price": "204.87",
        "price_per_adult": {
          "total_fare": "204.87",
          "tax": "147.87"
        },
        "restrictions": {
          "refundable": false,
          "change_penalties": true
        }
      }
    },
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
                "departs_at": "2016-11-28T16:15",
                "arrives_at": "2016-11-28T20:15",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "ATH"
                },
                "marketing_airline": "A3",
                "operating_airline": "A3",
                "flight_number": "841",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 7
                }
              },
              {
                "departs_at": "2016-11-28T22:30",
                "arrives_at": "2016-11-28T23:20",
                "origin": {
                  "airport": "ATH"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "A3",
                "operating_airline": "A3",
                "flight_number": "7136",
                "aircraft": "321",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 7
                }
              }
            ]
          }
        }
      ],
      "fare": {
        "total_price": "205.45",
        "price_per_adult": {
          "total_fare": "205.45",
          "tax": "73.45"
        },
        "restrictions": {
          "refundable": false,
          "change_penalties": true
        }
      }
    },
    {
      "itineraries": [
        {
          "outbound": {
            "flights": [
              {
                "departs_at": "2016-11-25T09:50",
                "arrives_at": "2016-11-25T12:15",
                "origin": {
                  "airport": "SKG"
                },
                "destination": {
                  "airport": "IST",
                  "terminal": "I"
                },
                "marketing_airline": "TK",
                "operating_airline": "TK",
                "flight_number": "1882",
                "aircraft": "738",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "W",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T15:45",
                "arrives_at": "2016-11-25T17:10",
                "origin": {
                  "airport": "IST",
                  "terminal": "I"
                },
                "destination": {
                  "airport": "DUS"
                },
                "marketing_airline": "TK",
                "operating_airline": "TK",
                "flight_number": "1527",
                "aircraft": "333",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "W",
                  "seats_remaining": 9
                }
              }
            ]
          },
          "inbound": {
            "flights": [
              {
                "departs_at": "2016-11-28T11:35",
                "arrives_at": "2016-11-28T16:55",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "IST",
                  "terminal": "I"
                },
                "marketing_airline": "TK",
                "operating_airline": "TK",
                "flight_number": "1524",
                "aircraft": "32B",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "W",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-28T20:05",
                "arrives_at": "2016-11-28T20:30",
                "origin": {
                  "airport": "IST",
                  "terminal": "I"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "TK",
                "operating_airline": "TK",
                "flight_number": "1893",
                "aircraft": "73H",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "W",
                  "seats_remaining": 9
                }
              }
            ]
          }
        },
        {
          "outbound": {
            "flights": [
              {
                "departs_at": "2016-11-25T09:50",
                "arrives_at": "2016-11-25T12:15",
                "origin": {
                  "airport": "SKG"
                },
                "destination": {
                  "airport": "IST",
                  "terminal": "I"
                },
                "marketing_airline": "TK",
                "operating_airline": "TK",
                "flight_number": "1882",
                "aircraft": "738",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "W",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T15:45",
                "arrives_at": "2016-11-25T17:10",
                "origin": {
                  "airport": "IST",
                  "terminal": "I"
                },
                "destination": {
                  "airport": "DUS"
                },
                "marketing_airline": "TK",
                "operating_airline": "TK",
                "flight_number": "1527",
                "aircraft": "333",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "W",
                  "seats_remaining": 9
                }
              }
            ]
          },
          "inbound": {
            "flights": [
              {
                "departs_at": "2016-11-28T07:40",
                "arrives_at": "2016-11-28T13:05",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "IST",
                  "terminal": "I"
                },
                "marketing_airline": "TK",
                "operating_airline": "TK",
                "flight_number": "1530",
                "aircraft": "321",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "W",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-28T20:05",
                "arrives_at": "2016-11-28T20:30",
                "origin": {
                  "airport": "IST",
                  "terminal": "I"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "TK",
                "operating_airline": "TK",
                "flight_number": "1893",
                "aircraft": "73H",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "W",
                  "seats_remaining": 9
                }
              }
            ]
          }
        }
      ],
      "fare": {
        "total_price": "210.32",
        "price_per_adult": {
          "total_fare": "210.32",
          "tax": "207.32"
        },
        "restrictions": {
          "refundable": false,
          "change_penalties": true
        }
      }
    },
    {
      "itineraries": [
        {
          "outbound": {
            "flights": [
              {
                "departs_at": "2016-11-25T16:15",
                "arrives_at": "2016-11-25T16:20",
                "origin": {
                  "airport": "SKG"
                },
                "destination": {
                  "airport": "BEG",
                  "terminal": "2"
                },
                "marketing_airline": "JU",
                "operating_airline": "JU",
                "flight_number": "523",
                "aircraft": "319",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T18:05",
                "arrives_at": "2016-11-25T19:55",
                "origin": {
                  "airport": "BEG",
                  "terminal": "2"
                },
                "destination": {
                  "airport": "ZRH"
                },
                "marketing_airline": "JU",
                "operating_airline": "JU",
                "flight_number": "374",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T20:50",
                "arrives_at": "2016-11-25T22:05",
                "origin": {
                  "airport": "ZRH"
                },
                "destination": {
                  "airport": "DUS"
                },
                "marketing_airline": "JU",
                "operating_airline": "AB",
                "flight_number": "8283",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 4
                }
              }
            ]
          },
          "inbound": {
            "flights": [
              {
                "departs_at": "2016-11-28T09:35",
                "arrives_at": "2016-11-28T11:40",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "BEG",
                  "terminal": "2"
                },
                "marketing_airline": "JU",
                "operating_airline": "JU",
                "flight_number": "321",
                "aircraft": "319",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 4
                }
              },
              {
                "departs_at": "2016-11-28T13:05",
                "arrives_at": "2016-11-28T15:10",
                "origin": {
                  "airport": "BEG",
                  "terminal": "2"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "JU",
                "operating_airline": "JU",
                "flight_number": "522",
                "aircraft": "319",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 9
                }
              }
            ]
          }
        }
      ],
      "fare": {
        "total_price": "219.10",
        "price_per_adult": {
          "total_fare": "219.10",
          "tax": "119.10"
        },
        "restrictions": {
          "refundable": false,
          "change_penalties": true
        }
      }
    },
    {
      "itineraries": [
        {
          "outbound": {
            "flights": [
              {
                "departs_at": "2016-11-25T16:15",
                "arrives_at": "2016-11-25T16:20",
                "origin": {
                  "airport": "SKG"
                },
                "destination": {
                  "airport": "BEG",
                  "terminal": "2"
                },
                "marketing_airline": "JU",
                "operating_airline": "JU",
                "flight_number": "523",
                "aircraft": "319",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T18:05",
                "arrives_at": "2016-11-25T19:55",
                "origin": {
                  "airport": "BEG",
                  "terminal": "2"
                },
                "destination": {
                  "airport": "ZRH"
                },
                "marketing_airline": "JU",
                "operating_airline": "JU",
                "flight_number": "374",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T20:50",
                "arrives_at": "2016-11-25T22:05",
                "origin": {
                  "airport": "ZRH"
                },
                "destination": {
                  "airport": "DUS"
                },
                "marketing_airline": "JU",
                "operating_airline": "AB",
                "flight_number": "8283",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 4
                }
              }
            ]
          },
          "inbound": {
            "flights": [
              {
                "departs_at": "2016-11-28T06:40",
                "arrives_at": "2016-11-28T07:50",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "ZRH"
                },
                "marketing_airline": "JU",
                "operating_airline": "AB",
                "flight_number": "8454",
                "aircraft": "321",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 4
                }
              },
              {
                "departs_at": "2016-11-28T09:30",
                "arrives_at": "2016-11-28T11:10",
                "origin": {
                  "airport": "ZRH"
                },
                "destination": {
                  "airport": "BEG",
                  "terminal": "2"
                },
                "marketing_airline": "JU",
                "operating_airline": "JU",
                "flight_number": "371",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-28T13:05",
                "arrives_at": "2016-11-28T15:10",
                "origin": {
                  "airport": "BEG",
                  "terminal": "2"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "JU",
                "operating_airline": "JU",
                "flight_number": "522",
                "aircraft": "319",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "E",
                  "seats_remaining": 9
                }
              }
            ]
          }
        }
      ],
      "fare": {
        "total_price": "232.83",
        "price_per_adult": {
          "total_fare": "232.83",
          "tax": "132.83"
        },
        "restrictions": {
          "refundable": false,
          "change_penalties": true
        }
      }
    },
    {
      "itineraries": [
        {
          "outbound": {
            "flights": [
              {
                "departs_at": "2016-11-25T16:00",
                "arrives_at": "2016-11-25T16:55",
                "origin": {
                  "airport": "SKG"
                },
                "destination": {
                  "airport": "VIE"
                },
                "marketing_airline": "LH",
                "operating_airline": "OS",
                "flight_number": "6441",
                "aircraft": "E95",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T17:35",
                "arrives_at": "2016-11-25T19:15",
                "origin": {
                  "airport": "VIE"
                },
                "destination": {
                  "airport": "DUS"
                },
                "marketing_airline": "LH",
                "operating_airline": "OS",
                "flight_number": "6355",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 9
                }
              }
            ]
          },
          "inbound": {
            "flights": [
              {
                "departs_at": "2016-11-28T10:10",
                "arrives_at": "2016-11-28T11:50",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "VIE"
                },
                "marketing_airline": "LH",
                "operating_airline": "OS",
                "flight_number": "6354",
                "aircraft": "321",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-28T12:35",
                "arrives_at": "2016-11-28T15:20",
                "origin": {
                  "airport": "VIE"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "LH",
                "operating_airline": "OS",
                "flight_number": "6442",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 9
                }
              }
            ]
          }
        }
      ],
      "fare": {
        "total_price": "233.87",
        "price_per_adult": {
          "total_fare": "233.87",
          "tax": "163.87"
        },
        "restrictions": {
          "refundable": false,
          "change_penalties": true
        }
      }
    },
    {
      "itineraries": [
        {
          "outbound": {
            "flights": [
              {
                "departs_at": "2016-11-25T16:00",
                "arrives_at": "2016-11-25T16:55",
                "origin": {
                  "airport": "SKG"
                },
                "destination": {
                  "airport": "VIE"
                },
                "marketing_airline": "LH",
                "operating_airline": "OS",
                "flight_number": "6441",
                "aircraft": "E95",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T19:45",
                "arrives_at": "2016-11-25T20:50",
                "origin": {
                  "airport": "VIE"
                },
                "destination": {
                  "airport": "MUC",
                  "terminal": "2"
                },
                "marketing_airline": "LH",
                "operating_airline": "OS",
                "flight_number": "6329",
                "aircraft": "319",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-25T21:30",
                "arrives_at": "2016-11-25T22:40",
                "origin": {
                  "airport": "MUC",
                  "terminal": "2"
                },
                "destination": {
                  "airport": "DUS"
                },
                "marketing_airline": "LH",
                "operating_airline": "LH",
                "flight_number": "2024",
                "aircraft": "32A",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "T",
                  "seats_remaining": 9
                }
              }
            ]
          },
          "inbound": {
            "flights": [
              {
                "departs_at": "2016-11-28T10:10",
                "arrives_at": "2016-11-28T11:50",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "VIE"
                },
                "marketing_airline": "OS",
                "operating_airline": "OS",
                "flight_number": "152",
                "aircraft": "321",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "K",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-28T12:35",
                "arrives_at": "2016-11-28T15:20",
                "origin": {
                  "airport": "VIE"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "OS",
                "operating_airline": "OS",
                "flight_number": "809",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "K",
                  "seats_remaining": 9
                }
              }
            ]
          }
        }
      ],
      "fare": {
        "total_price": "235.20",
        "price_per_adult": {
          "total_fare": "235.20",
          "tax": "178.20"
        },
        "restrictions": {
          "refundable": false,
          "change_penalties": true
        }
      }
    },
    {
      "itineraries": [
        {
          "outbound": {
            "flights": [
              {
                "departs_at": "2016-11-25T16:00",
                "arrives_at": "2016-11-25T16:55",
                "origin": {
                  "airport": "SKG"
                },
                "destination": {
                  "airport": "VIE"
                },
                "marketing_airline": "OS",
                "operating_airline": "OS",
                "flight_number": "810",
                "aircraft": "E95",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "V",
                  "seats_remaining": 5
                }
              },
              {
                "departs_at": "2016-11-25T17:35",
                "arrives_at": "2016-11-25T19:15",
                "origin": {
                  "airport": "VIE"
                },
                "destination": {
                  "airport": "DUS"
                },
                "marketing_airline": "OS",
                "operating_airline": "OS",
                "flight_number": "155",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "V",
                  "seats_remaining": 5
                }
              }
            ]
          },
          "inbound": {
            "flights": [
              {
                "departs_at": "2016-11-28T10:10",
                "arrives_at": "2016-11-28T11:50",
                "origin": {
                  "airport": "DUS"
                },
                "destination": {
                  "airport": "VIE"
                },
                "marketing_airline": "OS",
                "operating_airline": "OS",
                "flight_number": "152",
                "aircraft": "321",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "K",
                  "seats_remaining": 9
                }
              },
              {
                "departs_at": "2016-11-28T12:35",
                "arrives_at": "2016-11-28T15:20",
                "origin": {
                  "airport": "VIE"
                },
                "destination": {
                  "airport": "SKG"
                },
                "marketing_airline": "OS",
                "operating_airline": "OS",
                "flight_number": "809",
                "aircraft": "320",
                "booking_info": {
                  "travel_class": "ECONOMY",
                  "booking_code": "K",
                  "seats_remaining": 9
                }
              }
            ]
          }
        }
      ],
      "fare": {
        "total_price": "249.87",
        "price_per_adult": {
          "total_fare": "249.87",
          "tax": "171.87"
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
