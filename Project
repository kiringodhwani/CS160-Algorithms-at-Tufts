#########################################################
##  Implementation of HW 5 Question 1, CS160 Spring22  ##
#########################################################

import sys

# Input: array (of ints) of stone damage values, and dragon health value (int)
# Returns: integer, the minimum number of stones needed to kill the dragon
# Implemented using top-down dynamic programming
def magic_stones_topdown(stones, health):
    # define the dp array
    MS = [sys.maxsize] * (health + 1)
    return magic_stones_topdown_helper(stones, MS, health)

# Helper for magic_stones_topdown
def magic_stones_topdown_helper(stones, MS, health):
    # define length of the stones array
    n = len(stones)

    # Base case/s
    # If health = 0 we do not need any stones (we have killed the dragon)
    if health == 0:
        return 0
    
    # When the value in the memoization table that corresponds with the 
    # original inputted health value is filled in, we have found the answer.
    if MS[health] != sys.maxsize:
        return MS[health]
    
    # Initialize the minimum number of stones to infinity. We do this because
    # any valid set of stones is less than infinity, so we can easily update
    # this value when we find a valid set of stones
    min = sys.maxsize

    # Try all stones less than the current health value. This ensures that we
    # never use stones that would cause the dragon's health to drop below 0
    # (this was a base case in the homework problem).
    for i in range(0, n):
        if stones[i] <= health:
            prev_min = magic_stones_topdown_helper(stones, MS, health - stones[i])


            # Check if we need to replace the current min. Of course, we have
            # to add 1 to the previous min to account for the 1 stone used to
            # get from the previous min to the current min.
            if prev_min != sys.maxsize and prev_min + 1 < min:
                min = prev_min + 1
    
    # We will store the minimum number of stones for each health value in a
    # memoization table
    MS[health] = min

    return min


# Input: array (of ints) of stone damage values, and dragon health value (int)
# Returns: integer, the minimum number of stones needed to kill the dragon
# Implemented using bottom-up dynamic programming
def magic_stones_bottomup(stones, health):
    # define length of the stones array
    n = len(stones)

    # define DP array
    MS = [0 for i in range(health+1)]

    # Base case/s
    # If health = 0 we do not need any stones (we have killed the dragon)
    MS[0] = 0

    # Initialize table values to infinity
    for i in range(1, health+1):
        MS[i] = sys.maxsize
    
    # Compute minimum stones required for all values 1...health
    for i in range(1, health+1):
        for j in range(n):
            # Loop through set of stones smaller than the current health value
            # which is equal to i. This ensures that we never use stones that
            # would cause the dragon's health to drop below 0 (this was a base
            # case in the homework problem).
            if (stones[j] <= i):
                prev_min = MS[i - stones[j]]

                # Decide if we need to replace the current min at index i. Of
                # course, we have to add 1 to the previous min to account for
                # the 1 stone used to get from the previous min to the current
                # min.
                if (prev_min != sys.maxsize and prev_min + 1 < MS[i]):
                    MS[i] = prev_min + 1
    
    return MS[health]
            

#########################################################
##  Implementation of HW 2 Question 2, CS160 Spring22  ##
#########################################################

# Input: array of integers
# Returns: integer, the number of flips in the array
def count_flips(arr):
    n = len(arr)

    # Initialize a temporary array of length n, set all values in array to 0
    temp = [0]*n

    return mergeSort(arr, temp, 0, n - 1)

# Input: An array of integers, a temporary array, the left and right bounds
#        of the array to be parsed
# Returns The number of flips in the array
# Purpose: This function uses a modified version of mergeSort to count the
#          number of flips in the array
def mergeSort(arr, temp, left, right):

    num_flips = 0

    if left < right:
        # Define a mid variable to divide the array in half, we calculate
        # mid with floor division 
        mid = (left + right)//2

        # Recursively call mergeSort on the left half of the current array
        num_flips += mergeSort(arr, temp, left, mid)

        # Recursively call mergeSort on the right half of the current array
        num_flips += mergeSort(arr, temp, mid + 1, right)

        # Merge the right and left subarrays into one merged, sorted subarray
        num_flips += merge(arr, temp, left, right, mid)
    
    return num_flips

# Input: An array of integers, a temporary array, the start point of the left
#        subarray, the endpoint of the right subarray, the split point
#        between the left and right subarrays
# Returns: The number of flips found while merging
# Purpose: Merges two subarrays into one sorted array
def merge(arr, temp, left, right, mid):

    # define starting indices of the left subarray, the right subarray, and 
    # the to-be-merged, sorted array
    l_start = left
    r_start = mid + 1
    m_start = left

    num_flips = 0

    while l_start <= mid and r_start <= right:
        # If the current value in the left subarray is less than the current
        # value in the right subarray (i.e. arr[l_start] <= arr[r_start]),
        # then there are no flips. To add to the forming sorted array, we add
        # the current value in the left subarray since it is the smaller of
        # the two and then move onto the next value in the left subarray and
        # look to insert into the next open spot in the merged array
        if arr[l_start] <= arr[r_start]:
            temp[m_start] = arr[l_start]
            l_start += 1
            m_start += 1
        
        # If the current value in left subarray is greater than the current 
        # value in the right subarray, then we have found a flip. To add to
        # the merged array, we add the current value in the right subarray
        # since it is smaller.
        else:
            temp[m_start] = arr[r_start]
            # Since we know the array is sorted, the current value in the right
            # subarray will also have flips with all of the values in the left
            # subarray to the right of the current value in the left subarray
            # (since all of the values to the right of the current one are
            # greater than it). The number of values to the right of the
            # current value in the left subarray is equal to mid - lstart. 
            # Thus, we increment num_flips by this value plus 1 to account for
            # the current value in the left subarray.
            num_flips += (mid - l_start + 1)
            r_start += 1
            m_start += 1
    # Move remaining elements of left subarray into the temp array
    while l_start <= mid:
        temp[m_start] = arr[l_start]
        l_start += 1
        m_start += 1
        
    # Move remaining elements of right subarray into the temp array
    while r_start <= right:
        temp[m_start] = arr[r_start]
        r_start += 1
        m_start += 1
        
        # Copy sorted temp array into original array
    for i in range(left, right + 1):
        arr[i] = temp[i]
        
    return num_flips
