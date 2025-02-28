# FLAMES-Using-python
def flames_game(name1, name2):
    # Clean the names by removing spaces and converting to lowercase
    name1 = name1.replace(" ", "").lower()
    name2 = name2.replace(" ", "").lower()

    # Count the unique letters in both names
    for char in set(name1):
        if char in name2:
            # Remove common characters
            count = min(name1.count(char), name2.count(char))
            name1 = name1.replace(char, '', count)
            name2 = name2.replace(char, '', count)

    # Calculate the total remaining characters
    total_remaining = len(name1) + len(name2)

    # FLAMES list
    flames = ['F', 'L', 'A', 'M', 'E', 'S']

    # Determine the relationship
    while len(flames) > 1:
        index = (total_remaining - 1) % len(flames)  # Get the index to remove
        flames.pop(index)  # Remove the character at that index

    # Return the relationship based on the last remaining letter
    result = flames[0]
    if result == 'F':
        return "Friends"
    elif result == 'L':
        return "Lovers"
    elif result == 'A':
        return "Affectionate"
    elif result == 'M':
        return "Marriage"
    elif result == 'E':
        return "Enemies"
    elif result == 'S':
        return "Siblings"

# Example usage
if __name__ == "__main__":
    name1 = input("Enter the first name: ")
    name2 = input("Enter the second name: ")
    result = flames_game(name1, name2)
    print(f"The relationship is: {result}")
