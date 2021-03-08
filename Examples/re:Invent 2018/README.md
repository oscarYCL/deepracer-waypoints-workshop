# Waypoints reward function for the:Invent 2018
## Racing Line
![reinvent_base](https://user-images.githubusercontent.com/61004532/110326203-4e589080-8053-11eb-8f23-d7d9948696b4.png)
## Reward function
```python
def reward_function(params):

    center_variance = params["distance_from_center"] / params["track_width"]
    #racing line
    left_lane = [23,24,50,51,52,53,61,62,63,64,65,66,67,68]#Fill in the waypoints
    
    center_lane = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,25,26,27,28,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,54,55,56,57,58,59,60,69,70]#Fill in the waypoints
    
    right_lane = [29,30,31,32,33,34]#Fill in the waypoints
    
    #Speed
    fast = [0,1,2,3,4,5,6,7,8,9,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70]#Fill in the waypoints, 2m/s
    slow = [10,11,12,13,14,15,16,17,18,19,20,21,22,23,24]#Fill in the waypoints, 1m/s
    
    reward = 21

    if params["all_wheels_on_track"]:
        reward += 10
    else:
        reward -= 10

    if params["closest_waypoints"][1] in left_lane and params["is_left_of_center"]:
        reward += 10
    elif params["closest_waypoints"][1] in right_lane and not params["is_left_of_center"]:
        reward += 10
    elif params["closest_waypoints"][1] in center_lane and center_variance < 0.4:
        reward += 10
    else:
        reward -= 10
    if params["closest_waypoints"][1] in fast:
        if params["speed"] == 2 :
            reward += 10
        else:
            reward -= 10
    elif params["closest_waypoints"][1] in slow:
        if params["speed"] == 1 :
            reward += 10
        else:
            reward -= 10
        
    
    return float(reward)
```
## Training configuration(4 hours by default Hyperparameter)
<img width="970" alt="螢幕截圖 2021-03-08 下午9 35 15" src="https://user-images.githubusercontent.com/61004532/110328426-4f3ef180-8056-11eb-858b-891e5a91203f.png">
<img width="969" alt="螢幕截圖 2021-03-08 下午9 37 39" src="https://user-images.githubusercontent.com/61004532/110328668-988f4100-8056-11eb-939f-8e2c37072788.png">


## Evaluation results 

## Racing Video
