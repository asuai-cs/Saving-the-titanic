# Saving-the-titanic
# This project simulates an autopilot system to navigate the Titanic and avoid icebergs. This is a special project which could have saved the titanic ship from hitting the iceberg by determining the iceberg position.
# titanic_autopilot.py
def get_all_positions():
    return [(i, j) for i in range(10) for j in range(10)]

def get_cell(row, col):
    if row == 3 and col == 3:
        return "🧊"
    return "🌊"

def find_iceberg_position():
    # This function finds the iceberg position
    for row, col in get_all_positions():
        value = get_cell(row, col)
        if value == "🧊":
            return (row, col)

def auto_pilot_next_step(titanic_pos, ocean_size):
    iceberg_pos = find_iceberg_position()
    if iceberg_pos[0] == titanic_pos[0]:
        if titanic_pos[0] == 0:
            # Escape to the south if can't go north
            return "SOUTH"
        return "NORTH"
    return "WEST"

ocean_size = 10
initial_iceberg_pos = [3, 3]
initial_titanic_pos = [3, 8]

# The Scenario
next_step = auto_pilot_next_step(initial_titanic_pos, ocean_size)
print(f"The Titanic should move: {next_step}")

