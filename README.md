<img src="https://github.com/CLHollis/Election_Analysis/blob/main/images/Vote_Colorado.jpg?raw=true" width="700" height="350">[^1]

# Election Analysis

## Project Overview 
A Colorado Board of Elections employee has given you the following tasks to complete the election audit of a recent local congressional election. 

1.	Calculate the total number of votes cast.
2.	Get a complete list of candidates who received votes and counties that voted.
3.	Calculate the total number of votes each candidate received.
4.	Calculate the percentage of votes each candidate won.
5.	Calculate which county had the highest voter turnout.
6.	Determine the winner of the election based on popular vote.

## Resources
-	Data Source: [election_results.csv](https://github.com/CLHollis/Election_Analysis/blob/main/Resources/election_results.csv)
-	Software: Python 3.7.6, Visual Studio Code, 1.63.0

## Results 
[Results in text format](https://github.com/CLHollis/Election_Analysis/blob/main/analysis/election_results.txt) | [Code for Analysis](https://github.com/CLHollis/Election_Analysis/blob/main/PyPoll_challenge.py)

<image src="https://github.com/CLHollis/Election_Analysis/blob/main/images/electionResults.PNG?raw=true" width="450" height="600">[^2]  

| ⭐ The winner of the election was **Diana DeGette** | 🗳️ The largest County Turnout was **Denver** |
| --- | --- |
| <image src="https://github.com/CLHollis/Election_Analysis/blob/main/images/Diana_Degette.jpg?raw=true" width="400" height="250">[^3] | <image src="https://github.com/CLHollis/Election_Analysis/blob/main/images/Denver_Skyline.jpg?raw=true" width="450" height="275">[^4] |

## Summary
This script can be used—with some modifications—for any election. 
- One way is to use a different data set with the same criteria (counties, votes, and/or candidtates) but adding raw data for these criteria. For example, adding another candidate, gathering more votes, or adding more counties. 
- Another way is to find the breakdown of another variable of the voters such as: ethnicity, income, gender, or any other census-type question that is asked on the ballot and tracked. First you would initialize a variable for the new criteria, like "voter_ethnicity." Then repeat the code from the county (or candidate) stats, but substitute in your new variable. For example, replace the word "county" for "voter_ethnicity."     
    
## Technical Syntax

- **Find number of total votes:**
    ```
    # Initialize a total vote counter.
    total_votes = 0
    
    # Print and save to text file.
    f"Total Votes: {total_votes:,}
    print(election_results, end="")
    txt_file.write(total_votes)
    ```
    
- **Find County Vote count and percentage:**  * *"County: percentage of total votes (total number of votes)"* *
    ```
    # Create a county list and county votes dictionary.
    county_name = []
    county_votes = {}
    
        # Inside the for loop, going row buy row, Extract the county name from each row.
        county = row[1]
    
        # Write an if statement that checks that the county does not match any existing county in the county list.
        if county not in county_name:
            # Add the existing county to the list of counties.
            county_name.append(county)
            # Begin tracking the county's vote count.
            county_votes[county] = 0
        # Add a vote to that county's vote count.
         county_votes[county] += 1
    
    # Write a for loop to get the county from the county dictionary.
    with open(file_to_save, "w") as txt_file:
        election_results = (
            f"\nElection Results\n"
            f"-------------------------\n"
            f"Total Votes: {total_votes:,}\n"
            f"-------------------------\n"
            f"County Votes:\n"
        )
        print(election_results, end="")
        txt_file.write(election_results)
        # 6a: Write a for loop to get the county from the county dictionary.
        for county in county_votes:
        
        # Retrieve the county vote count.
        area_votes = county_votes[county]
        
        # Calculate the percentage of votes for the county.
        county_vote_percentage = float(area_votes) / float(total_votes) * 100
        county_results = (
            f"{county}: {county_vote_percentage:.1f}% ({area_votes:,})\n")

         # Print the county results to the terminal.
        print(county_results)

         # Save the county votes to a text file.
        txt_file.write(county_results)

         # Write an if statement to determine the winning county and get its vote count.
        if (area_votes > most_votes):
            most_votes = area_votes
            largest_county = county
    ```
    
- **Which county had the largest number of votes?**
    ```
    # Print the county with the largest turnout to the terminal.
    winning_county_summary = (
        f"-------------------------\n"
        f"Largest County Turnout: {largest_county}\n"
        f"---------------------------------\n")
    print(winning_county_summary)

    # Save the county with the largest turnout to a text file.
    txt_file.write(winning_county_summary)
    ```
    
- **Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.**
    ```
    # Save the final candidate vote count to the text file.
    for candidate_name in candidate_votes:

        # Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the
        # terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)
    ```
    
- **Which candidate won the election, what was their vote count, and what was their percentage of the total votes?**
    ```
        # Determine winning vote count, winning percentage, and candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage

    # Print the winning candidate (to terminal)
    winning_candidate_summary = (
        f"-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)

    # Save the winning candidate's name to the text file
    txt_file.write(winning_candidate_summary)
    ```

------------------------------------------------------------------
[^1]: [Community Resource Center. "Voting in Colorado – Every Election Matters"](https://crcamerica.org/programs/participation-project/voter-registration-and-updating/). Accessed Dec. 9, 2021.
[^2]: [Results Sccreenshot](https://github.com/CLHollis/Election_Analysis/blob/main/images/electionResults.PNG). Created Dec. 9, 2021.
[^3]: [Channel 4 CBS Denver. "Rep. Diana DeGette To Run For Democratic Leadership In Congress"](https://denver.cbslocal.com/2018/11/07/diana-degette-democratic-whip-congress/). Accessed Dec. 9, 2021.
[^4]: [WaterNow Alliance. "WaterNow Alliance is Breaking Ground in Colorado"](https://waternow.org/2018/07/31/waternow-alliance-is-breaking-ground-in-colorado/). Accessed Dec. 9, 2021.
-----------------------------------------------------------------

