#  Media Streaming Service 🎞️
Let's Define every part ---> 🎬
1. [Requirements Analysis](#Requirements_Analysis)
2. [EER Diagrams](#EER_Diagrams)
3. [UML Diagrams](#UML_Diagrams)


## Requirements Analysis 🎯

***Main entities & Their attribute & DataType*** : 

* **UserProfiles**  
  + _UserID_ (_Primary key_) _:UUID_
  + _UserName_ _:String_
  + _Password_ _:String_
*  **SubscriptionDetails** 
   + _SubscriptionID_ (_Primary key_) _:UUID_
   + _UserID_ (_Foreign key_) _:UUID_
   + _StartSubscriptionDate_ _:Date_
   + _EndSubscriptionDate_ _:Date_
   + _SubscriptionTier_ _:String_
* **PaymentHistories**
     + _PaymentID_ (_Primary key_) _:UUID_
     + _UserID_ (_Foreign key_) _:UUID_
     + _SubscriptionID (_Foreign key_)  _:UUID_
     + _TransactionDetails_ _:String_
* **WatchLaterList**
     + _WatchLaterListID_ (_Primary Key_) _:UUID_
     + _UserID_ (_Foreign key_) _:UUID_
     + MediaAssets_ (_Foreign key_) _:UUID_
* **MediaAssets**
   +  _MediaAssetsID_(_Primary Key_) _:UUID_
   + _ProductionCompanyID_(_Foreign Key_) _:UUID_
   + _StorageLocationID_ (_Foreign key_) _:UUID_
   + _Genre_ _:String_
   + _Title_ _:String_
   + _ProductionYear_ _:Integer_
   + _AverageRatingScore_ _:Double_
   + _Director_ _:String_
   + _TypeMoviesORSeries_ _:String_
   + _ActorsList_ _:Array_
   + _ProducersList_ _:Array_
*  **Movies**
   + _MovieID_(_Primary Key_) _:UUID_
 * **Series**
   + _SeriesID_(_Primary Key_) _:UUID_
*  **ProductionCompany**
   + _ProductionCompanyID_ (_Primary Key_)_:UUID_
   + _Name_ _:String_
   + _YearOfEstablishment_ _:Integer_
   + _ContactInformation_ _:String_
* **Comment**
  + _CommentID_ (_Primary Key_) _:UUID_
  +  _UserID_ (_Foreign key_) _:UUID_
  + _MediaAssetsID_ (_Foreign key_) _:UUID_
  + _CommentInformation_ _:String_
* **Rating**
	+ _RatingID_ (_Primary Key_) _:UUID_
	+  _UserID_ (_Foreign key_) _:UUID_
	+  _MediaAssetsID_ (_Foreign key_) _:UUID_
	+ _RatingScore_ _:Double_
* **SeriesEpisode**
  + _EpisodeID_ (_Primary Key_) _:UUID_
  + _SeriesID_ (_Foreign key_) _:UUID_
  +  _MediaAssetsID_ (_Foreign key_) _:UUID_
  + _EpisodeNO_ _:String_
* **StorageLocation**
   + _StorageLocationID_ (_Primary key_) _:UUID_
  + _Server_ _:String_
  + _FilePath_ _:String_
  
  ***Description Of  Their RelationsShip*** : 
 
1. Each User has one Subscription Detail and Each Subscription Detail is available for one user (1..1:1..1)

2.  Each User has Many Payment Histories and Payment History is available for one user (1..1:0..N)

3. Each Subscription Detail has Many Payment Histories and Each Payment History is have one Subscription Detail (1..1:1..N)

4. Each user has one WatchLaterList and Each WatchLater movies can selected by Each User(1..1:1..1)

5.  Every Media in WatchLaterList contains many Media and Every Media can be in many WatchLaterList(0..N:0..M)

6. Each Media is made by one Production Company and Each Production Company can produce many Media(1..1:1..N)

7. Each Media has one Storage Location and one Storage Location can stored multiple Media items (1..1:1..N)

8. Movies and series are disjoint from MediaAssets ; Because MediaAssets should be one of them and can't be 2 of them simultaneously  and also they are Generalization of MediaAssets too

9. I get ProducersList and ActorsList as compositions because they contain additional details like name and age, etc

10. This part is Ternary because Each User can leave many comments on MediaAssets  (1..1:0..N) and Each Comment belongs to one MediaAsset and one User (1..1:0..N) and the end part as we said If users can leave multiple comments on the same MediaAsset the user-media relationship is many-to-many via comments (0..N:0..M)

11. Each User can rate many Medias and Each Media has only one Rating from Each User (0..1:0..N) 
And as in Chapter 4 (I mean "Entity versus Attribute") in this part I have treated Rating as an Attribute instead Entity

12. SeriesEpisode is Composition from series and Each Series have multiple episodes (1..1:1..N)


  ## EER Diagrams 🎨
  <img src="img/EER.svg" alt="Media Streaming Service">
  
  ## UML Diagrams 🎨
  <img src="img/UML.svg" alt="Media Streaming Service">