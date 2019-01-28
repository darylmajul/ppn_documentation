## Hotel

### Booking Flows

Get familiar with the proper booking flow for your site and where to use our API data.

#### Booking a Hotel Flow

##### Merchant 

1. [AutoSuggestV2](#docs)  
Provide a list of suggested cities or airports based on the user's search input
2. [ResultsWithCacheV2](#docs)  
Retrieve cached rates and hotel IDs based on the user's search criteria
3. [HotelDetails](#docs) (optional)  
Retrieve all details about the property the user has selected
4. [Rates.Live.Multi](#docs)  
Displaying live property rates and availability for 1 or 2 hotel IDs
5. [ContractRequest](#docs)  
Confirms the rate that the user has selected
6. [BookRequest](#docs)  
Sends customer and payment information to confirm their property booking
7. [BookDetails](#docs)  
Retrieves the post-book details

##### Closed User Group (CUG)

1. [AutoSuggestV2](#docs)  
Provide a list of suggested cities or airports based on the user's search input
2. [Express.Results](#docs)  
Returns a list of up to 100 properties matching the search criteria.
3. [Express.MultiContract](#docs) (optional)  
Returns multiple applicable rates from the property selected.
4. [Express.Book](#docs)  
Passes user and payment information and responds with a success or fail

#### Cancel a Booking

##### Merchant

1. [BookDetails](#docs)  
Gets the all details from the booking that was selected
2. [CancelRequest](#docs)  
Cancels a booking

#### Important Tips

##### Merchant

- Rates.Live.Multi limited to 5,000 calls per hour.
- Best practice is to leave nothing out. If a function returns it, display it.
- Do not hard code card_type in ContractRequest.
- Total booking days requirement:
    - greater than 1 day
    - less than or equal to 21 days
    - Not more than 329 days in advance.
- Always call run BookDetails after BookRequest so post-book page is displayed for the customer.

##### Closed User Group (CUG)

- Express.Results limited to 5,000 calls per hour
- Full path *Look to Book* ratio limited to 2000:1.
- Total booking days requirement: 
    - greater than 1 day
    - less than or equal to 21 days 
    - Not more than 350 days in advance
- ppn_bundle are not to be cached 
- Clearly display all required information to the traveler such as: price, property_fee, taxes, Cancellation details, Important Information
- If acting as the Merchant or Record, pass a static email address that will receive ALL correspondence related to the reservations.

#### Hotel Insurance Flow - Standalone

This API feature separates the insurance from the product, and allows the purchase of insurance for an unknown hotel booking.

- [Insurance Quote](#docs)  
Response will return a block of HTML that can be placed within the front end code and offers insurance to the customer
- [Insurance Purchase](#docs)  
If the customer selects "Yes" to buying insurance, *and the hotel reservation was successful*, you can then submit an insurance purchase.
- [Insurance Note Decline](#docs)  
If the customer selects "No" to buying insurance, *and the hotel reservation was successful*, it is required that you submit an insurance note decline request.
- [Insurance Lookup](#docs)  
Along with the method to retrieve hotel reservation details, an API call can be made to get details on the insurance purchase.




