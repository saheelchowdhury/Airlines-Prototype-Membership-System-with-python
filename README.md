# Airlines-Prototype-Membership-System-with-python
# Coding a tier based membership system with reward systems for an airlines using python

# Initial welcome message
```
print("Welcome to the Python Airlines Prototype Membership System")
print()
```
# Input prompts
```
first_name      = input("What is your first name?")
annual_miles    = input("How many miles have you flown this year?")
annual_segments = input("How many segments have you flown this year?")
annual_dollars  = input("How much money have you spent this year(USD)?")
lifetime_miles  = input("How many lifetime miles have you flown?")
lounge_response = input("Is your next flight to (or through) the Chicago airport?")
```
# Checking if the user is going to be eligible for using the Chicago airport's lounge
```
if lounge_response.strip().lower() in ["yes", "y"]:
        lounge_check = True
else:
        lounge_check = False
```
# Creating the prompt for ticket prices
```
ticket_price = input("How much will a Coach Class ticket for your next flight cost (USD)?")

print()
```
# Updating the variables to correct data types
```
first_name = str(first_name)
annual_miles = int(annual_miles)
annual_segments = int(annual_segments)
annual_dollars = float(annual_dollars)
lifetime_miles = int(lifetime_miles)
ticket_price = float(ticket_price)
```
# Updating the membership tiers and annual criteria 

<img width="600" alt="Screenshot 2024-01-30 at 2 43 24 AM" src="https://github.com/saheelchowdhury/Airlines-Prototype-Membership-System-with-python/assets/153671296/99f8166d-0b92-4b40-bf0d-e75cdb07b3a5">

```
if   annual_miles >= 100000 or (annual_segments >= 120 and annual_dollars >= 24000):
     annual_tier = "Diamond" 
elif annual_miles >= 75000 or (annual_segments >= 90 and annual_dollars >= 15000):
     annual_tier = "Ruby"
elif annual_miles >= 50000 or (annual_segments >= 60 and annual_dollars >= 7000):
     annual_tier = "Emerald"
elif annual_miles >= 25000 or (annual_segments >= 30 and annual_dollars >= 3000):
     annual_tier = "Sapphire" 
else: annual_tier = "None" 
```
# Updating the membership tiers and lifetime criteria 

<img width="600" alt="Screenshot 2024-01-30 at 2 45 31 AM" src="https://github.com/saheelchowdhury/Airlines-Prototype-Membership-System-with-python/assets/153671296/6496502b-6b38-4096-a54e-f42f53aa9b54">

```
if   lifetime_miles >= 3000000:
     lifetime_tier = "Diamond"
elif lifetime_miles >= 2000000:
     lifetime_tier = "Ruby"
elif lifetime_miles >= 1000000:
     lifetime_tier = "Emerald"
else:lifetime_tier = "None"
```
# Coding to always determine the highest tire
```
highest_tier = "None"

if "Diamond" in (annual_tier, lifetime_tier):
    highest_tier = "Diamond" 
elif "Ruby" in (annual_tier, lifetime_tier):
    highest_tier = "Ruby" 
elif "Emerald" in (annual_tier, lifetime_tier):
    highest_tier = "Emerald" 
elif "Sapphire" in (annual_tier, lifetime_tier):
    highest_tier = "Sapphire"
```
# Coding the reward based membership tier rubric

<img width="600" alt="Screenshot 2024-01-30 at 2 50 25 AM" src="https://github.com/saheelchowdhury/Airlines-Prototype-Membership-System-with-python/assets/153671296/5770244a-0581-49a7-b293-3d3971ea8185">

```
if  highest_tier == "Diamond":
    number_of_free_bags = 3
    class_of_free_seat_upgrades = "First Class"
    free_lounge_access = True
    percent_discount_on_ticket_prices = 30
    
elif highest_tier == "Ruby":
    number_of_free_bags = 2
    class_of_free_seat_upgrades = "First Class"
    free_lounge_access = False
    percent_discount_on_ticket_prices = 25
    
elif highest_tier == "Emerald":
    number_of_free_bags = 1
    class_of_free_seat_upgrades = "Business Class"
    free_lounge_access = False
    percent_discount_on_ticket_prices = 20
    
elif highest_tier == "Sapphire":
    number_of_free_bags = 0
    class_of_free_seat_upgrades = "Business Class"
    free_lounge_access = False
    percent_discount_on_ticket_prices = 15
```
# Output summary so far 
```
print(f"{first_name}, this year, you have flown {annual_segments:,} flights for {annual_miles:,} miles and spent {annual_dollars:,} USD with Python Airlines. Lifetime, you have flown {lifetime_miles:,} miles.")
```

# To display message when passenger is neither an annual member nor a lifetime one
```
if "None" in (annual_tier,lifetime_tier):
    print(f"You are on your way to achieving annual frequent-flier status with Python Airlines!")
```
# Message to show in 3 cases : The passenger is part of a lifetime tier, just a part of annual tier and both 
```
if "Diamond" in (lifetime_tier):
    print (f"You have achieved lifetime frequent-flier status at the Diamond level!")
elif "Ruby" in (lifetime_tier):
    print (f"You have achieved lifetime frequent-flier status at the Ruby level!")
elif "Emerald" in (lifetime_tier):
    print (f"You have achieved lifetime frequent-flier status at the Emerald level!")
elif "None" == lifetime_tier and "None" != annual_tier:
    print(f"This year, you have achieved annual frequent-flier status at the {annual_tier} level!")

if "Diamond" in (lifetime_tier and annual_tier):
     print (f"This year, you have also achieved annual frequent-flier status at the Diamond level!")
elif "Ruby" in (lifetime_tier and annual_tier):
    print (f"This year, you have also achieved annual frequent-flier status at the Ruby level!")
elif "Emerald" in (lifetime_tier and annual_tier):
    print (f"This year, you have also achieved annual frequent-flier status at the Emerald level!")
elif "Sapphire" in (lifetime_tier and annual_tier):
    print (f"This year, you have also achieved annual frequent-flier status at the Sapphire level!")

print()
```
# Deciding what reward type to mention based on their highest tier 
```
if highest_tier != "None":
    print("You have unlocked the following rewards:")
    if number_of_free_bags > 0:
        print(f"- {number_of_free_bags} free checked bags per flight")
    if class_of_free_seat_upgrades != "None":
        print(f"- Free seat upgrades to {class_of_free_seat_upgrades}")
    if free_lounge_access:
        if lounge_check: 
            print("- Enjoy free access to the club lounge in Chicago on your next/upcoming flight!")
        else:
            print("- Free access to the club lounge next time flying to/through in Chicago")
    if percent_discount_on_ticket_prices > 0:
        discounted_price = ticket_price - (ticket_price * (percent_discount_on_ticket_prices / 100))
        print(f"- Your upcoming flight ticket price of ${ticket_price:.2f} USD was reduced by {percent_discount_on_ticket_prices}% to ${discounted_price:.2f} USD.")

print()
```
# END 
