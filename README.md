# Egg-drop
code to find the highest floor from which an egg can drop without breaking it
def find_critical_floor(max_floors=102, max_eggs=7):
    eggs = max_eggs
    low, high = 1, max_floors
    
    # Initial step size (optimal x)
    x = 14
    current_floor = x
    
    while eggs > 1:
        print(f"Dropping egg from floor {current_floor}...")
        if current_floor > max_floors:
            current_floor = max_floors  # Edge case
        
        # Simulate egg drop (replace with actual test)
        breaks = input("Did the egg break? (yes/no): ").strip().lower() == 'yes'
        
        if breaks:
            print("Egg broke! Moving down sequentially...")
            high = current_floor - 1
            eggs -= 1
            x -= 1
            current_floor = low + 1  # Next step: linear check
        else:
            print("Egg survived! Moving up...")
            low = current_floor
            current_floor += x - 1
            x -= 1
    
    # Last egg: linear search between low and high
    for floor in range(low, high + 1):
        print(f"Dropping egg from floor {floor}...")
        breaks = input("Did the egg break? (yes/no): ").strip().lower() == 'yes'
        if breaks:
            return floor - 1
    
    return high  # If no breaks at all

critical_floor = find_critical_floor()
print(f"The critical floor is: {critical_floor}")
