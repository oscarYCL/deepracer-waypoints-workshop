# Waypoints reward function for the LarsLoop
## Racing Line
![thunder_hill_open](https://user-images.githubusercontent.com/61004532/116771469-41b64e80-aa7e-11eb-8a78-31fd532a2254.png)



## Reward function
```python
def reward_function(params):

    center_variance = params["distance_from_center"] / params["track_width"]
    #racing line
    left_lane = [14,15,16,17,18,19,20,21,22,23,31,32,33,34,35,44,45,46,47,48,49,50,51,52,53,61,62]#Fill in the waypoints
    
    center_lane = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,24,25,30,36,37,38,43,54,55,56,57,58,59,60,63,64,65,66,67,68,69,70,71,72,78,79,80,81,82]#Fill in the waypoints
    
    right_lane = [26,27,28,29,39,40,41,42,73,74,75,76,77]#Fill in the waypoints
    
    #Speed
    fast = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82]#Fill in the waypoints, 2m/s
    slow = [18,19,20,21]#Fill in the waypoints, 1m/s
    
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
<img width="462" alt="螢幕截圖 2021-05-01 下午1 09 35" src="https://user-images.githubusercontent.com/61004532/116771491-804c0900-aa7e-11eb-95e9-aabb8ac0e77a.png">
<img width="969" alt="螢幕截圖 2021-05-01 下午1 11 53" src="https://user-images.githubusercontent.com/61004532/116771531-d0c36680-aa7e-11eb-866a-c37fbb10778c.png">

## Evaluation results 


## Racing Video (Time: 02:27)

