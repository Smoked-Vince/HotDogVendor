# ============================
# Start of Coursework
# ============================

# Used to observe execution time
import time


# ============================
# Create the data file
# ============================

with open("HotDogs.txt", "w") as my_file:

    # Format:
    # ID, Name, YearWeek, VeganSold, MeatSold, OnionsUsed, KetchupUsed

    # Dolly Dogs
    my_file.write("DD_056,Dolly Dogs,202313,40,140,10.5,1\n")
    my_file.write("DD_056,Dolly Dogs,202314,40,170,15.0,2\n")
    my_file.write("DD_056,Dolly Dogs,202315,60,100,14.5,1\n")
    my_file.write("DD_056,Dolly Dogs,202316,90,130,15.0,2\n")
    my_file.write("DD_056,Dolly Dogs,202317,40,170,25.5,4\n")
    my_file.write("DD_056,Dolly Dogs,202318,70,130,20.0,1\n")
    my_file.write("DD_056,Dolly Dogs,202319,50,180,15.5,4\n")
    my_file.write("DD_056,Dolly Dogs,202320,90,130,10.0,2\n")

    # Korner Kart
    my_file.write("KK_745,Korner Kart,202313,60,130,10.5,2\n")
    my_file.write("KK_745,Korner Kart,202314,30,130,10.0,4\n")
    my_file.write("KK_745,Korner Kart,202315,80,150,25.5,2\n")
    my_file.write("KK_745,Korner Kart,202316,30,140,25.0,3\n")
    my_file.write("KK_745,Korner Kart,202317,80,160,20.5,4\n")
    my_file.write("KK_745,Korner Kart,202318,90,170,25.0,1\n")
    my_file.write("KK_745,Korner Kart,202319,80,150,20.5,3\n")
    my_file.write("KK_745,Korner Kart,202320,90,180,25.0,4\n")

    # Echo Eats
    my_file.write("EE_867,Echo Eats,202313,70,100,26.5,3\n")
    my_file.write("EE_867,Echo Eats,202314,80,140,19.5,5\n")
    my_file.write("EE_867,Echo Eats,202315,100,50,20.0,2\n")
    my_file.write("EE_867,Echo Eats,202316,90,120,21.0,1\n")
    my_file.write("EE_867,Echo Eats,202317,90,170,10.0,1\n")
    my_file.write("EE_867,Echo Eats,202318,30,150,15.6,2\n")
    my_file.write("EE_867,Echo Eats,202319,55,100,14.5,3\n")
    my_file.write("EE_867,Echo Eats,202320,90,100,26.5,3\n")

    # Pocket Panda
    my_file.write("PP_306,Pocket Panda,202313,100,180,10.0,1\n")
    my_file.write("PP_306,Pocket Panda,202314,70,130,10.0,4\n")
    my_file.write("PP_306,Pocket Panda,202315,80,150,16.0,1\n")
    my_file.write("PP_306,Pocket Panda,202316,130,100,19.5,2\n")
    my_file.write("PP_306,Pocket Panda,202317,50,170,25.5,2\n")
    my_file.write("PP_306,Pocket Panda,202318,90,110,15.0,3\n")
    my_file.write("PP_306,Pocket Panda,202319,110,130,10.5,4\n")
    my_file.write("PP_306,Pocket Panda,202320,30,160,26.5,4\n")

    # Gideon Grub
    my_file.write("GG_237,Gideon Grub,202313,90,50,15.0,1\n")
    my_file.write("GG_237,Gideon Grub,202314,60,130,13.6,2\n")
    my_file.write("GG_237,Gideon Grub,202315,80,50,15.5,1\n")
    my_file.write("GG_237,Gideon Grub,202316,70,50,20.0,1\n")
    my_file.write("GG_237,Gideon Grub,202317,100,50,19.5,2\n")
    my_file.write("GG_237,Gideon Grub,202318,50,50,22.0,2\n")
    my_file.write("GG_237,Gideon Grub,202319,90,50,10.0,1\n")
    my_file.write("GG_237,Gideon Grub,202320,80,50,14.5,2\n")


# ============================
# Functions
# ============================

# Load vendor data from file
def load_data(filename):

    vendors = []

    try:
        with open(filename, "r") as file:

            for line in file:

                parts = line.strip().split(",")

                if len(parts) != 7:
                    continue

                vendor = {
                    "id": parts[0],
                    "name": parts[1],
                    "year_week": parts[2],
                    "vegan": int(parts[3]),
                    "meat": int(parts[4]),
                    "onions": float(parts[5]),
                    "ketchup": float(parts[6])
                }

                vendors.append(vendor)

    except FileNotFoundError:
        print("Error: File not found.")

    except ValueError:
        print("Error: Data format issue in file.")

    return vendors


# ============================
# Searching Functions
# ============================

# Linear search for unsorted data
def linear_search_unsorted(data, target_name):
    for vendor in data:
        if vendor["name"] == target_name:
            return vendor
    return None


# Linear search for sorted data
def linear_search_sorted(data, target_name):
    target_name = target_name.lower()
    for vendor in data:
        name = vendor["name"].lower()
        if name == target_name:
            return vendor
        elif name > target_name:
            return None
    return None

# Binary search
def binary_search(data, target_name):
    try:
        target_name = target_name.lower()
        low = 0
        high = len(data) - 1
        while low <= high:
            mid = (low + high) // 2
            name = data[mid]["name"].lower()
            if name == target_name:
                return data[mid]
            elif name < target_name:
                low = mid + 1
            else:
                high = mid - 1
        return None

    except (IndexError, KeyError, TypeError):
        print("Error: Try again")
        return None


# ============================
# Sorting Functions
# ============================

# Bubble sort
def bubble_sort(data):
    if data == None:
        raise ValueError("The input 'data' must be provided.")
    if type(data) != list:
        raise TypeError("The input 'data' must be a list.")
    n = len(data)
    if n <= 1:
        return data
    for i in range(n):
        for j in range(0, n - i - 1):
            if "name" not in data[j] or "name" not in data[j + 1]:
                raise KeyError("The key 'name' is missing.")
            if type(data[j]["name"]) != str:
                raise TypeError("Vendor names must be strings.")
            if data[j]["name"] > data[j + 1]["name"]:
                data[j], data[j + 1] = data[j + 1], data[j]


# Quick sort
def quick_sort(data):
    if len(data) <= 1:
        return data
    pivot = data[0]
    left = [item for item in data[1:] if item["name"] <= pivot["name"]]
    right = [item for item in data[1:] if item["name"] > pivot["name"]]
    return quick_sort(left) + [pivot] + quick_sort(right)


# Measure execution time
def measure_time(function, *args):
    start = time.perf_counter()
    result = function(*args)
    end = time.perf_counter()
    print(function.__name__, "execution time:", end - start)
    return result


# ============================
# Analysis Functions
# ============================

# Most productive vendor
def most_productive_vendor(data):
    totals = {}
    for vendor in data:
        name = vendor["name"]
        totals[name] = totals.get(name, 0) + vendor["vegan"] + vendor["meat"]
    return max(totals, key=totals.get)


# Vegan vs meat totals
def vegan_vs_meat(data):
    vegan_total = sum(vendor["vegan"] for vendor in data)
    meat_total = sum(vendor["meat"] for vendor in data)
    return vegan_total, meat_total

# Least ketchup used
def least_ketchup(data):
    return min(data, key=lambda x: x["ketchup"])


# Save results
def save_results(filename, results):
    with open(filename, "w") as file:
        file.write(results)


# ============================
# Main Code
# ============================

vendors = load_data("HotDogs.txt")


# ============================
# Sorting Efficiency Comparison
# ============================

print("\nSorting Efficiency Comparison")
measure_time(bubble_sort, vendors.copy())
sorted_vendors = measure_time(quick_sort, vendors.copy())


# ============================
# Search Section
# ============================

valid_names = sorted(set(v["name"] for v in vendors))
while True:
    search_name = input("Enter vendor name to search: ").strip()
    if not search_name:
        print("Invalid input. Try again.")
        continue
    result = binary_search(sorted_vendors, search_name)
    if result:
        print("\nVendor found:", result["name"])
        break
    else:

        print("\nVendor NOT found.")
        print("Available vendors:", ", ".join(valid_names))
        measure_time(linear_search_unsorted, vendors, search_name)
        measure_time(linear_search_sorted, sorted_vendors, search_name)
        measure_time(binary_search, sorted_vendors, search_name)


# ============================
# Search Efficiency Comparison
# ============================

print("\nSearch Efficiency Comparison")
measure_time(linear_search_unsorted, vendors, search_name)
measure_time(linear_search_sorted, sorted_vendors, search_name)
measure_time(binary_search, sorted_vendors, search_name)


# ============================
# Run Analysis Functions
# ============================

best_vendor = most_productive_vendor(vendors)
vegan, meat = vegan_vs_meat(vendors)
least = least_ketchup(vendors)
print("\nAnalysis Results")
print("Most productive vendor:", best_vendor)
print("Total vegan hotdogs:", vegan)
print("Total meat hotdogs:", meat)
print("Vendor using least ketchup:", least["name"])


# ============================
# Detailed Analysis Testing
# ============================

print("\n--- Testing Analysis Functions ---")

# Test 1
print("\nTest 1: Most Productive Vendor")
print("Expected: Vendor with highest combined sales")
print("Actual:", most_productive_vendor(vendors))


# Test 2
print("\nTest 2: Vegan vs Meat Totals")
vegan_total, meat_total = vegan_vs_meat(vendors)
print("Expected: Total vegan and meat hotdog sales")
print("Actual Vegan Total:", vegan_total)
print("Actual Meat Total:", meat_total)


# Test 3
print("\nTest 3: Least Ketchup Usage")
least_vendor = least_ketchup(vendors)
print("Expected: Vendor entry with smallest ketchup value")
print("Actual Vendor:", least_vendor["name"])
print("Ketchup Used:", least_vendor["ketchup"])


# Test 4
print("\nTest 4: Empty List Test")
empty_data = []
try:
    print(most_productive_vendor(empty_data))
except ValueError:
    print("Handled empty list correctly.")


# Test 5
print("\nTest 5: Single Vendor Test")
single_vendor = [
    {
        "id": "TEST_001",
        "name": "Test Vendor",
        "year_week": "202320",
        "vegan": 10,
        "meat": 20,
        "onions": 2.0,
        "ketchup": 1.0
    }
]

print("Most productive:", most_productive_vendor(single_vendor))
print("Vegan vs Meat:", vegan_vs_meat(single_vendor))
print("Least ketchup:", least_ketchup(single_vendor)["name"])


# ============================
# Save Results to File
# ============================

results = f"""
Most productive vendor: {best_vendor}
Total vegan hotdogs: {vegan}
Total meat hotdogs: {meat}
Vendor using least ketchup: {least['name']}
"""

save_results("analysis.txt", results)


# ============================
# Evidence of Persistent Storage
# ============================

print("\nContents of saved analysis file:")
with open("analysis.txt", "r") as file:
    print(file.read())
print("Persistent storage confirmed.")
