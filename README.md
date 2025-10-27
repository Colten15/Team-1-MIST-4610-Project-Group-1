# Team-1-MIST-4610-Project-Group-1

## Team Members:
1. Colten Lin cwl27381@uga.edu
2. Audrey Djunaidi ad04585@uga.edu
3. Max Trinh mlt22305@uga.edu
4. Claire Woehrman ctw49810@uga.edu
5. Nayan Magdum nm37036@uga.edu

## Problem Description:
The goal of this project is to build, design, and implement a relational database to model the key operations of Spotify's streaming ecosystem. The central entity in our model is the User entity, representing each spotify account holder. Each user may hold a subscription (Free, Student, or Premium), which is linked to billing records for payment tracking. Users can create multiple playlists, each containing songs across various genres and albums. These relationships are modeled to reflect how Spotify's users engage with artists and manage their music libraries. To simplify the database structure, we assume that each playlist is created by a single user, once a user buys a subscription they do not cancel it, each song belongs to exactly one genre, and each album is associated with a single artist. These assumptions allow us to maintain referential integrity and reduce many-to-many relationship complexisty in the model. We are interested in accurately modeling these relationships, generating sample data, and populating the entities and their attributes with this sample data. Furthermore, we plan to perform SQL queries to gain important business insights. These queries will demonstrate how the relational database can support Spotify's data driven decisions regarding marketing and user retention.


## Data Model:

Explanation of our Data Model:
Our data model is based on the structure of a music streaming platform that allows users to listen to songs, create playlists, and manage subscriptions. The goal of this design is to capture all the essential entities and their relationships in a system similar to Spotify or Apple Music.

The User entity represents individuals who use the platform. Each user has attributes such as their name, email, date of birth, and the type of subscription they hold. Each user can subscribe to multiple plans, and each subscription plan can be associated with various users. This many-to-many relationship between Users and Subscriptions allows for flexibility. Users may switch or hold multiple active plans (ex, family or student subscriptions), and the same subscription type can be shared among many users. Billing information is linked to both Users and Subscriptions through the Billing entity, which tracks details such as billing amount, date, and payment method.

The Playlist entity is connected to Users in a one-to-many relationship, since each user can create multiple playlists. Each playlist can contain various songs, and each song can appear in various playlists. This many-to-many relationship between Playlist and Songs is represented through the associative table playlistHasSong, which links songs to playlists.

Music data is organized through the Songs, Albums, Genre, Artists, and Label entities. Each Song includes attributes like title, length, and release date, and it belongs to both a specific Album and Genre. Each Album can contain many songs and is connected to one Artist, forming a one-to-many relationship. Genres represent musical categories such as pop, rock, or hip-hop, and each genre can be linked to many songs.

The Artists entity represents performers and songwriters, while Label captures the record companies they are signed with. Each label can have many artists, but each artist belongs to only one label. Since artists often collaborate on songs, the ArtistHasSong associative entity captures the many-to-many relationship between Artists and Songs.

Overall, the model provides a comprehensive structure to store and analyze user behavior, billing history, subscription patterns, and mustic metadata. It allows for meaningful insights into user activity (such as most played genres or playlists), financial performance through billing data, and artist collaboration networks within the music streaming world.

<img width="1033" height="739" alt="RD" src="https://github.com/user-attachments/assets/0a9ac47e-b413-4782-8d16-294b5b153622" />


## Data Dictionary:

<img width="1628" height="1093" alt="album" src="https://github.com/user-attachments/assets/c71a8c28-47b5-4730-8697-f68587587db4" />

<img width="1629" height="770" alt="artisthassong" src="https://github.com/user-attachments/assets/8edba8f7-6275-46fe-9a26-731e690cf94e" />

<img width="1630" height="1198" alt="artists" src="https://github.com/user-attachments/assets/6bed1d19-ada5-4687-8f55-71e2485f8510" />

<img width="1628" height="1174" alt="billing" src="https://github.com/user-attachments/assets/453dcc22-8d13-4ddd-b9ee-8d50bb04d481" />

<img width="1628" height="761" alt="genre" src="https://github.com/user-attachments/assets/d50ccca3-80c9-416c-9c70-82d710acffdc" />

<img width="1627" height="948" alt="label" src="https://github.com/user-attachments/assets/bff11298-e1c3-47d0-9b7d-87b01012fe95" />

<img width="1628" height="905" alt="playlist" src="https://github.com/user-attachments/assets/e5bb77b1-86e4-4373-a6c6-bf874b66438e" />

<img width="1625" height="531" alt="playlisthassong" src="https://github.com/user-attachments/assets/40e4f046-2092-4142-9bd9-863c49578a4f" />

<img width="1469" height="1245" alt="songs" src="https://github.com/user-attachments/assets/cc4c686a-0695-41ab-ac79-389973754ce9" />

<img width="1628" height="733" alt="subscription (2)" src="https://github.com/user-attachments/assets/a361a4f4-0082-469d-823e-10aaba4790f5" />

<img width="1466" height="820" alt="users" src="https://github.com/user-attachments/assets/d8dc88aa-1f14-4ad3-af55-9615e4fbc2b8" />


## Queries:

![queries](https://github.com/user-attachments/assets/b7826d30-c7c0-48a9-a67c-aa3d1f5a3940)


1. This query retrieves each user's first and last name along with their associated subscription type.
<img width="2243" height="1002" alt="image" src="https://github.com/user-attachments/assets/f04fe6d9-980c-4598-a813-6a769c32b3d1" />
By joining the Users and Subscription tables, we can easily see which customers belong to which subscription plan. This information allows managers to evaluate the distribution of customers across subscription tiers such as Free, Student, Family, and Premium.

2. This query displays all songs along with the genre they belong to by joining the Songs and Genre tables. In this case, the filter limits the output to the "Pop" genre.
IMAGE HERE: <img width="2252" height="769" alt="image" src="https://github.com/user-attachments/assets/2d045507-b967-4934-8355-3d94d690e7f2" />
This type of query is useful for curating playlists, analyzing the catalog composition, or targeting users who prefer specific genres. It ensures that the music database is well organized and that songs are properly categorized for user discovery and recommendation algorithms

3. This query retrieves all artists signed under a specific label, here Universal Music, by joining the artists and Label tables using labelId.
<img width="2140" height="733" alt="image" src="https://github.com/user-attachments/assets/972062a7-ae6d-4baa-a7a9-3204aa7be927" />
This query is useful for record label managers and analysts to view their roster of artists or to generate reports for a particular label. It can help identify which artists    belong to major or independent labels, support label-based marketing campaigns, and provide insight into how artists are distributed across different music labels in the system.

4. This query produces a combined view of song information, including song title, album name, artist names, and genre.
<img width="1057" height="441" alt="image" src="https://github.com/user-attachments/assets/1e385205-ba3d-4f92-95b0-d61dcddf458c" />
By joining the Songs, Album, Artists, and Genre tables it creates a complete dataset that represents the full metadata of each track. This comprehensive view is useful for data validation, catalog management, and internal reporting. It ensures that every song is correctly associated with its artist and album, providing a foundation for features like search, recommendations, and playist creation.

5. This query calculates the total revenue generated for each subscription type by summing up all billing amounts associated with each plan. It joins the Subscription and Billing tables through subscriptionId, groups the results by subscription type, and orders them in descending order of total revenue.
<img width="2075" height="468" alt="image" src="https://github.com/user-attachments/assets/909df6cb-e29e-4e85-aad2-00b942e0f362" />
This query is useful for identifying which subscription tiers contribute the most to overall revenue. It helps management evaluate financial performance, optimize pricing strategies, and make data-driven decisions to maximize profitability.

6. This query retrieves all playlists created by a specific user, in this case Colten Walker, along with the date each playlist was created. It joins the Playlist and Users tables using userId to match playlists with their creators.
<img width="2060" height="740" alt="image" src="https://github.com/user-attachments/assets/bc345ee7-ef8d-40f8-b3c6-9079f2ee6da3" />
This information helps users or managers view an individual’s playlist activity and organization over time. It can also be extended to include song counts or ordering by song duration to analyze playlist structure, user engagement, and music preferences.

7. This query identifies the most popular songs based on how many times they appear in playlists. By joining the Songs and playlistHasSong tables through songId, it counts the number of playlist inclusions for each track, orders them by popularity, and limits the result to the top ten songs.
<img width="1809" height="703" alt="image" src="https://github.com/user-attachments/assets/867ac2f4-9768-4ad1-a256-e7abd323a940" />
This query is valuable for recognizing trending songs that users frequently add to their playlists. It can inform promotional campaigns, personalized recommendations, and data-driven insights into current listener preferences.


8. This query lists the song title, genre, and number of songs that has similar phrasing to it using a REGEXP
<img width="978" height="568" alt="image" src="https://github.com/user-attachments/assets/86cfb740-fe60-4835-a42d-a6af884d9b95" />
This query helps can allow artists and creative directors, labels, and songwriters to search in a database songs with similar titles or similar phrasing/wording within titles. For instance, the REGEXP function can be used to search for songs with titles that start with "The" as a means to differentiate titles within albums or between artists. In this case above, given the current limited database of songs, we used the example in which a song would start with the letter "A" in which there is one song. This query in theory would be useful for larger databases with more songs. 

9. This query lists all songs whose duration is longer than the average length of all songs in the database. It uses a subquery to calculate the overall average song length and compares each song’s duration against that value.
<img width="1837" height="707" alt="image" src="https://github.com/user-attachments/assets/b18c685e-7a31-478a-85c3-7d03dbe28f03" />
This query helps identify longer tracks within the catalog, which can be useful for playlist curation, understanding song length trends, or optimizing streaming recommendations based on track duration patterns.

10. This query calculates the total revenue generated by each record label. It traces the relationships from Label through Artists, Songs, Playlists, Users, Subscription, and Billing tables to link each label to the subscription payments made by users who listen to their artists’ songs. The results are grouped by label and ordered by total revenue in descending order.
<img width="1970" height="833" alt="image" src="https://github.com/user-attachments/assets/e308c5f9-dfaf-4188-b9b7-2ca7a9b2c8cf" />
This query provides valuable insights into which record labels contribute the most to platform revenue. It helps managers evaluate label performance, negotiate partnerships, and make informed decisions about artist promotion and royalty distribution.

## Database Information:
Name of the database: ns_Group1

Additional Info: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();
