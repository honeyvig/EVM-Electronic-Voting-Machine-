# EVM-Electronic-Voting-Machine
Types of EVM (Electronic Voting Machines)

There are mainly two types of EVMs used in India and other countries:

    Direct Recording Electronic (DRE) Voting Machines:
        These are machines that directly record votes electronically without the need for paper ballots.
        Example: The EVM used in India with two main components – the Control Unit (CU) and the Ballot Unit (BU).

    Optical Scan Voting Systems:
        These are used in some countries and involve the use of optical scanners to read paper ballots.
        In this system, voters mark their choices on paper ballots, and an optical scanner counts the votes.

Components of EVM (Electronic Voting Machine)

An EVM typically consists of the following components:

    Control Unit (CU):
        It is used by the election officer to manage the voting process. It stores the information on votes and ensures that voting is secure.
        The Control Unit can only be accessed by the election officer, and it controls the Ballot Unit.

    Ballot Unit (BU):
        It is where the voter presses a button to cast their vote. Each button corresponds to a candidate or a political party. The Ballot Unit is connected to the Control Unit via a cable.

    Voter Verifiable Paper Audit Trail (VVPAT):
        This is an additional feature attached to EVMs in some countries, including India, for added transparency. It provides a paper trail of the vote cast by the voter, which can be verified by the voter after casting their vote.

    Voter Display Unit (VDU):
        It displays the names and symbols of the candidates/parties for voters to choose from.

EVM Working Process (Python Simulation)

The working of an EVM can be simulated with a Python program that mimics the process of voting, vote counting, and tampering detection. Here's a simplified version of an EVM simulation.

class EVM:
    def __init__(self, candidates):
        self.candidates = candidates  # List of candidates
        self.votes = {candidate: 0 for candidate in candidates}  # Dictionary to store votes

    def vote(self, voter_id, candidate):
        if candidate in self.candidates:
            self.votes[candidate] += 1
            print(f"Vote registered for {candidate} by voter {voter_id}.")
        else:
            print("Invalid candidate selected.")
    
    def count_votes(self):
        print("\nVote Count:")
        for candidate, count in self.votes.items():
            print(f"{candidate}: {count} votes")

# Simulate EVM voting
def simulate_evm():
    candidates = ["Alice", "Bob", "Charlie"]
    evm = EVM(candidates)

    # Simulate votes
    evm.vote(1, "Alice")
    evm.vote(2, "Bob")
    evm.vote(3, "Alice")
    evm.vote(4, "Charlie")
    evm.vote(5, "Bob")
    
    # Count the votes
    evm.count_votes()

# Run the simulation
simulate_evm()

This Python program simulates a simple Electronic Voting Machine (EVM) where voters cast votes for candidates. It keeps track of votes and then counts them after all votes are cast.
Possible Ways in Which EVMs Can Be Tampered or Hacked

Although modern EVMs are designed with several layers of security, there have been concerns and allegations about the tampering or hacking of these devices. Some ways in which EVMs could potentially be tampered with include:

    Manipulation of the Software (Firmware Hacking):

        Hackers could attempt to manipulate the EVM's firmware to change the way votes are recorded. This could involve altering the machine's software to count votes for specific candidates.

        Device/Tools Used: Computers, USB drives, specialized programming equipment (such as JTAG devices for hardware hacking).

    Physical Tampering:

        Physical tampering can occur if someone has access to the EVM before or after the election. This could include switching the EVM, inserting modified hardware into the machine, or installing backdoors in the Control Unit or Ballot Unit.

        Device/Tools Used: Specialized hardware (e.g., modified control units, USB devices, Malicious chips).

    Network-Based Hacking:

        In systems that are connected to the internet or local networks, cyber-attacks could compromise the system.

        Device/Tools Used: Computers, Wi-Fi or Ethernet connections, and remote access tools.

    VVPAT Manipulation:

        If a Voter Verifiable Paper Audit Trail (VVPAT) system is present, it could be tampered with to print incorrect paper trails or substitute legitimate votes with fake ones.

        Device/Tools Used: Tampered VVPAT devices, remote access to printing equipment.

    Malicious Third-Party Equipment:
        Malicious third-party devices like a USB flash drive can be inserted into the EVM to extract or manipulate the data.

Potential Python Program to Simulate Hacking

If someone were to tamper with the system, we could simulate the process of vote manipulation. This Python code demonstrates a potential tampering scenario, where an unauthorized actor attempts to alter the vote counts.

import random

class HackedEVM(EVM):
    def hack_vote(self):
        # Randomly selects a candidate and manipulates the vote count
        manipulated_candidate = random.choice(self.candidates)
        self.votes[manipulated_candidate] += random.randint(1, 10)  # Adds random votes
        print(f"Votes for {manipulated_candidate} have been manipulated.")

# Simulate Hacked EVM
def simulate_hacked_evm():
    candidates = ["Alice", "Bob", "Charlie"]
    evm = HackedEVM(candidates)

    # Simulate votes
    evm.vote(1, "Alice")
    evm.vote(2, "Bob")
    evm.vote(3, "Alice")
    evm.vote(4, "Charlie")
    evm.vote(5, "Bob")

    # Hack the votes
    evm.hack_vote()
    
    # Count the votes after tampering
    evm.count_votes()

# Run the simulation of tampering
simulate_hacked_evm()

Explanation of the Hacked EVM Program:

    The HackedEVM class extends the EVM class and introduces a method called hack_vote that manipulates the vote count of a randomly chosen candidate by adding a random number of votes.
    The program then simulates votes, manipulates them through the hack, and counts the final results.

Conclusion

EVMs are crucial for modern elections, but their security is a significant concern, as they can be vulnerable to hacking, both digitally and physically. Understanding how tampering works can help us improve the systems and ensure fair elections. While Python simulations can show us how voting and tampering might work, ensuring real-world security requires rigorous testing, monitoring, and multiple layers of security to protect voting machines.
