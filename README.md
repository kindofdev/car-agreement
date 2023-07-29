# 🚗 CarAgreement 🚗
CarAgreement is a car delivery agreement business flow between a manufacturer and a dealer built in Daml.

### I. Overview
This project was created by using the `empty-skeleton` template. The project adopts and exemplifies the `proposal-accept` design pattern.

Manufacturer can create a CarOffer contract visible for dealer. Manufacturer can withdraw a
CarOffer previously created. Dealer can exercise her right either Reject or Accept the offer. In case dealer Accept the offer needs to provide a proper Cert issued by an issuer pointed by manufacturer and an Iou issued by a bank pointed by manufacturer in the offer with sufficient amount to cover the price. The result of accepting an offer are: (1) a DeliverCarAgreement between dealer and manufacturer created, (2) an iou with price own by manufacturer and (3) an optional iou own by dealer with the remaining amount in case dealer provides an iou with amount greater that price. CarOffer can be accepted multiple times, generating multiple agreements for delivering multiple cars.


### II. Workflow
  1. manufacturer creates a CarOffer.
  2. bank credits dealer an Iou with the amount equals to price in the offer.
  3. issuer (the one pointed by manufacturer in the offer) generates a cert for dealer.
  4. dealer Accept the offer passing Iou own by dealer and Cert own by dealer. This results
     in (1) an Iou own by manufacturer with price amount, (2) a DeliverCarAgreement contract created and the initial Iou provided by dealer being archived.

### III. Compiling & Testing
```
$ daml build
$ daml test
```

### IV. Running
```
$ daml start
```