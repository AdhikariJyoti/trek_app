# trek_app
##This app contains REST API.
REST APIs have functionalities to add trek destination,get trek destinations,update trek destination and delete trek destination.

1) POST a trek destination:This adds a trek destination:
  -URL:
    http://127.0.0.1:5000/rest/treks
  -URL endpoint:
    /rest/treks
  -Method:
    POST
  -Parameters:
    title:required:text:title of trek destination
    days:required:number:days required to complete trek destination
    difficulty:required:text:difficulty level of trek destination
    total_cost:required:number:total cost of trek destination
    token:required:text: token of logged in user
    
   -Payload{
    "title":"sikles trek",
    "days":5,
    "difficulty":"level 1",
    "total_cost":20000,
    "token":"6e13ac4a-eafd-4d55-8d21-0efba897be2e"
      }
    -Response:
      message:a message after adding of trek destination is attempted
     e.g:
     >if adding of trek destination is successful:
     {
        "message": "Trek has been added Successfully"
      }
      OR.
      >if entered token is invalid/user is not authenticated:
      {
        "message": "Please enter a valid token"
      }
      
2)GET all treks-this gets all treks from database
  -URL:
    http://127.0.0.1:5000/rest/treks
  -URL endpoint:
    /rest/treks
  -Method:
    GET
  -Parameters:
    No parameteres required as input.
    
  
  -Response:
      logged_in_user:this returns if the request is sent by a logged in user or not ,returns NULL if user is not a logged in user.
      treks:This returns treks list which contains trekId, title of trek,days of trek, difficulty level of trek,total cost of trek,upvotes of trek and fullname of user who added              trek
      
   -E.g. -on successful response 200 OK
      Payload
      {
        "logged_in_user": null,
        "treks": [
            [
                3,
                "Phoksundo Trek",
                11,
                "level 4",
                24000,
                23,
                "Jyoti Adhikari"
            ],
            [
                4,
                "Khaptad trip",
                20,
                "level 4",
                20000,
                23,
                "Bigyan Rijal"
            ]

  ]
}

3)UPDATE - to update a trek destination
  -URL:
    http://127.0.0.1:5000/rest/treks
  -URL endpoint:
    /rest/treks
  -Method:
    PUT
  -Parameters:
    trekId:required:number:id of trek destination
    title:required:text:title of trek destination
    days:required:number:days required to complete trek destination
    difficulty:required:text:difficulty level of trek destination
    total_cost:required:number:total cost of trek destination
    token:required:text: token of logged in user
    
   -Payload
    {
    "trekId":12,
    "title":"tilicho lake trek",
    "days":5,
    "difficulty":"level 1",
    "total_cost":15000,
    "token":"6e13ac4a-eafd-4d55-8d21-0efba897be2e"
    }
    -Response:
      message:a message after updating of trek destination is attempted
     e.g:
     >if updating of trek destination is successful:
     {
        "message": "Trek has been updated Successfully"
      }
      OR.
      >if entered token is invalid/user is not authenticated:
      {
        "message": "Please enter a valid token"
      }
      OR.
      ->if user tries to update trek destination using someone else's token
      {
         "message": "you cannot update someone else's trek"
      }
      
4)DELETE - to delete a trek destination
  -URL:
    http://127.0.0.1:5000/rest/treks
  -URL endpoint:
    /rest/treks
  -Method:
    DELETE
  -Parameters:
    trekId:required:number:id of trek destination
    token:required:text: token of logged in user
    
   -Payload
    {
    "trekId":12,
    "token":"6e13ac4a-eafd-4d55-8d21-0efba897be2e"
    }
    -Response:
      message:a message after deleting of a trek destination is attempted
     e.g:
     >if updating of trek destination is successful:
     {
        "message": "Trek has been deleted Successfully"
      }
      OR.
      >if entered token is invalid/user is not authenticated:
      {
        "message": "Please enter a valid token"
      }
      OR.
      ->if user tries to delete trek destination using someone else's token
      {
         "message": "you cannot delete someone else's trek"
      }

      
    
  
    
