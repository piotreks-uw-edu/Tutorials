# GET request
import requests
response = requests.get("https://api.stackexchange.com/2.3/questions?\
                        order=desc&sort=activity&tagged=django\
                        &site=stackoverflow")
question = response.json()['items'][0]
title = question['title']
user_id = question['owner']['user_id']
display_name = question['owner']['display_name']
response = requests.get("https://api.stackexchange.com/2.3/users/{}?\
                        order=desc&sort=reputation&site=stackoverflow"
                        .format(user_id))
creation_date = response.json()['items'][0]['creation_date']
print("{} created on {} asked \"{}\"".format(display_name,
                                             creation_date,
                                             title))
											 
											 