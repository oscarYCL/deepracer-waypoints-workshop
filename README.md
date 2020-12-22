# AWS DeepRacer Free Student Workshop: Run faster by using your custom waypoints
# Reward Function

```python
def reward_function(params):
    #racing line
    center_variance = params["distance_from_center"] / params["track_width"]

    left_lane = []#Fill in the waypoints
    
    center_lane = []#Fill in the waypoints
    
    right_lane = []#Fill in the waypoints
    #Speed
    fast = []#Fill in the waypoints
    slow = []#Fill in the waypoints
    
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
## Wokrshop Guideline
https://www.linkedin.com/pulse/aws-deepracer-free-student-workshop-run-faster-using-your-cheuk-lam/?published=t
## Demo Video
https://youtu.be/__NjsBY2TS0
## Other Workshop
[AWS Educate Classroom for a free AWS DeepRacer Student Workshop](https://www.linkedin.com/pulse/aws-educate-classroom-free-deepracer-student-workshop-yuen-oscar/?trackingId=Ug9v8CodQdG7MXETAri5Ww%3D%3D)
