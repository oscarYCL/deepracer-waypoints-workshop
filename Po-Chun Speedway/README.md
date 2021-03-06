
# Reward function for the Po-Chun Speedway
## Racing Line
![penbay_open](https://user-images.githubusercontent.com/61004532/110137027-58884e00-7e0b-11eb-8c0d-dd712517157f.png)

## Reward function
```python
def reward_function(params):

    center_variance = params["distance_from_center"] / params["track_width"]

    left_lane = [3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,91,114,115,116,139,140,141,142,143,144,145,146,147,148,149,150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,184,185,186,187,188,189,190,191]#Fill in the waypoints
    
    center_lane = [0,1,2,48,49,50,51,52,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,92,93,94,95,96,97,103,104,105,106,107,108,109,110,111,112,113,117,118,119,120,121,122,123,124,125,126,127,128,129,130,131,132,133,134,135,136,137,138,192,193,194,195,196,197,198,199,200,201,202,203,204,205,206,207,208,209,210,211,212,213,214,220,221,222,223,224,225,226,227,228,229,230]#Fill in the waypoints
    
    right_lane = [53,54,98,99,100,101,102,215,216,217,218,219]#Fill in the waypoints
    
    fast = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,78,79,80,81,82,83,84,85,86,87,88,89,90,91,92,93,94,95,96,97,98,99,100,101,102,103,104,105,106,107,108,109,110,111,112,113,117,118,119,120,121,122,123,124,125,126,127,128,129,130,131,132,133,134,135,136,137,138,139,140,141,142,143,144,145,146,147,148,149,150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,184,185,186,187,188,189,190,191,192,193,194,195,196,197,198,199,200,201,202,203,204,205,206,207,208,209,210,211,212,213,214,215,216,217,218,219,220,221,222,223,224,225,226,227,228,229,230]#Fill in the waypoints
    slow = [74,75,76,77]#Fill in the waypoints
    
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
## Training configuration(5hours by default Hyperparameter)
<img width="961" alt="螢幕截圖 2021-03-06 下午9 00 01" src="https://user-images.githubusercontent.com/61004532/110207565-4b2c9b80-7ebf-11eb-97fd-68ffa9325577.png">
<img width="965" alt="螢幕截圖 2021-03-06 下午2 54 19" src="https://user-images.githubusercontent.com/61004532/110198256-2a971e00-7e8c-11eb-854c-3a19cf42a615.png">
## Evaluation results 
<img width="499" alt="Evaluation results" src="https://user-images.githubusercontent.com/61004532/110197175-bad16500-7e84-11eb-864a-1c487320f4d7.png">

## Racing Video (Time 02:27)
[![IMAGE ALT TEXT](http://img.youtube.com/vi/upiIGe60vGQ/0.jpg)](http://www.youtube.com/watch?v=upiIGe60vGQ)


