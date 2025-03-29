# truck-tracking-system
import time
import random

class Truck:
    def __init__(self, truck_id, location=(0, 0)):
        self.truck_id = truck_id
        self.location = location

    def update_location(self):
        # Simulating GPS coordinates change
        delta_x = random.uniform(-0.01, 0.01)
        delta_y = random.uniform(-0.01, 0.01)
        self.location = (self.location[0] + delta_x, self.location[1] + delta_y)

    def get_location(self):
        return self.location


def track_trucks(trucks):
    while True:
        print("\n--- Truck Locations ---")
        for truck in trucks:
            truck.update_location()
            print(f"Truck {truck.truck_id}: Location {truck.get_location()}")
        time.sleep(2)  # Update every 2 seconds


if __name__ == "__main__":
    trucks = [Truck(truck_id=i) for i in range(1, 6)]  # Tracking 5 trucks
    track_trucks(trucks)
