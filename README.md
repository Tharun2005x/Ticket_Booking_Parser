🎫 Smart Ticket Booking --- Corpus-Based NLP Sentence Parser

CSE 306 --- Mini Project | Basic Natural Language Processing

A simple rule-based NLP sentence parser for a ticket-booking domain.
The project demonstrates fundamental NLP concepts such as
tokenization, word-role/POS identification, corpus-based sentence
validation, rule-based parsing, and basic corpus learning using plain
Python.

📌 Project Overview

The Smart Ticket Booking NLP System works with a small corpus of
English sentences related to ticket booking.

The system can:

✅ Check whether an input sentence exists in the defined corpus.

❌ Reject sentences that are not present in the corpus.

🔤 Tokenize an input sentence into individual words.

🏷️ Identify the grammatical role of each word.

🧠 Learn new words by allowing the user to classify them.

➕ Add new sentences to the corpus.

💾 Save the updated corpus to a JSON file.

📋 Display the current corpus.

📊 Analyze word-role distribution across the corpus.

The project intentionally avoids heavy NLP libraries such as NLTK
and spaCy so that the underlying NLP logic remains easy to
understand and explain.

🎯 Objectives

The main objectives are to:

Understand basic NLP preprocessing.

Implement simple tokenization using Python.

Perform basic word-role/POS identification.

Implement a simple rule-based parser.

Validate sentences against a predefined corpus.

Allow the corpus and word dictionary to grow.

Store the updated corpus using JSON.

Perform a simple analysis of grammatical-role distribution.

🧠 NLP Concepts Used

1. Tokenization

Tokenization breaks a sentence into individual word tokens.

Example:

The user books a ticket

becomes:

["The", "user", "books", "a", "ticket"]

The project uses Python's built-in split() operation instead of an
external NLP tokenizer.

2. Word-Role / POS Identification

The system identifies roles such as:

Determiner

Noun -- Subject

Verb

Noun -- Object

Pronoun

Adjective

For the standard corpus sentences, the parser follows this pattern:

Determiner → Noun (Subject) → Verb → Determiner → Noun (Object)

Example:

The user books a ticket

Word     Role

The      Determiner
user     Noun - Subject
books    Verb
a        Determiner
ticket   Noun - Object

3. Corpus-Based Sentence Validation

The input sentence is normalized by:

Removing extra whitespace

Removing ., ?, and ! at the end

Converting text to lowercase

The normalized sentence is then compared with the corpus.

If it exists:

Status: ACCEPTED

Otherwise:

Status: REJECTED
Reason: not in my corpus

4. Rule-Based Parsing

The project uses a fixed five-word grammar pattern:

[Determiner, Subject Noun, Verb, Determiner, Object Noun]

Because the corpus follows this structure, word roles can be identified
based on their position.

This is a rule-based approach, not a machine-learning POS tagger.

📊 Dataset / Corpus

The project contains 20 initial ticket-booking sentences.

Examples include:

The user books a ticket
The user pays the fare
The user picks a seat
The user gets the ticket
The user checks the train
The agent books the ticket
The agent checks the seat
The agent prints the ticket
The system checks the payment
The system stores the booking
The agent confirms the booking
The system confirms the payment

The corpus focuses on actions performed by:

User

Agent

System

🛠️ Technologies Used

Technology         Purpose

Python             Main programming language
Lists              Store corpus sentences
Dictionaries       Store word-role mappings
Sets               Store determiners
JSON               Persistent corpus storage
Matplotlib         Role-distribution visualization
Jupyter Notebook   Development and demonstration environment

External NLP Libraries

No heavy NLP library such as NLTK or spaCy is required.

⚙️ Project Workflow

                ┌─────────────────────┐
                │   Input Sentence    │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │     Tokenization    │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Normalize Sentence  │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Compare with Corpus │
                └──────────┬──────────┘
                           │
                  ┌────────┴────────┐
                  │                 │
               Exists            Not Found
                  │                 │
                  ▼                 ▼
             ACCEPTED           REJECTED
                  │            "not in my corpus"
                  ▼
             Word Roles
                  │
                  ▼
            Display Results

📁 Project Structure

NLP_CSE306_Ticket_Booking_Parser/
│
├── NLP_CSE306_Ticket_Booking_Parser.ipynb
├── ticket_corpus.json
└── README.md

ticket_corpus.json is created when the optional persistent-storage
section is executed.

🚀 Getting Started

Prerequisites

Install Python 3.x and Jupyter Notebook/JupyterLab.

Install Matplotlib if it is not already available:

pip install matplotlib

Run the Project

Clone or download the project.

Open the notebook:

jupyter notebook

Open:

NLP_CSE306_Ticket_Booking_Parser.ipynb

Run the cells from top to bottom.

🔍 Important Functions

tokenize()

Splits a sentence into individual tokens.

tokenize("The user books a ticket.")

Output:

['The', 'user', 'books', 'a', 'ticket']

normalize()

Converts a sentence into a standard form for comparison.

normalize("The User Books A Ticket.")

Output:

the user books a ticket

check_sentence()

Checks whether a sentence belongs to the corpus.

result = check_sentence("The user books a ticket", CORPUS)
show_result(result)

tag_sentence()

Assigns grammatical roles to words.

tag_sentence("The user books a ticket")

Expected structure:

The      → Determiner
user     → Noun - Subject
books    → Verb
a        → Determiner
ticket   → Noun - Object

train_word()

Adds a new word and its category to the word model.

train_word("passenger", "Noun")

add_sentence()

Adds a new sentence to the corpus and can ask the user to classify
previously unknown words.

CORPUS = add_sentence("The passenger books a ticket", CORPUS)

save_corpus()

Stores the current corpus in JSON format.

save_corpus(CORPUS)

load_corpus()

Loads a previously saved corpus.

CORPUS = load_corpus()

display_corpus()

Displays all sentences currently stored in the corpus.

display_corpus(CORPUS)

🧪 Example

Accepted Sentence

Input:

The user books a ticket

Output:

Sentence : The user books a ticket
Status   : ACCEPTED

Word roles:
The          -> Determiner
user         -> Noun - Subject
books        -> Verb
a            -> Determiner
ticket       -> Noun - Object

Rejected Sentence

For example, a sentence that is not present in the corpus:

The driver drives a car

Output:

Sentence : The driver drives a car
Status   : REJECTED
Reason   : not in my corpus

🧠 Learning New Words

When a new sentence contains an unknown word, the system asks the user
to classify it:

1. Noun
2. Pronoun
3. Verb
4. Adjective

For example:

New word: passenger

What is this word? Enter 1-4:

If the user selects 1:

Learned: passenger -> Noun

The word is then stored in the word model for future use.

💾 Persistent Storage

The project optionally stores the corpus in:

ticket_corpus.json

This allows newly added sentences to be saved and loaded later.

Example JSON structure:

[
  "The user books a ticket",
  "The user pays the fare",
  "The agent checks the seat"
]

📊 Analysis

The notebook includes a simple visualization of word-role distribution
across the corpus.

Since each standard sentence contains:

1 Determiner
1 Subject Noun
1 Verb
1 Determiner
1 Object Noun

the role counts follow the fixed grammar structure of the corpus.

The analysis uses:

Counter()

to count the roles and Matplotlib to visualize the results.

🔬 Key Findings

A fixed sentence pattern makes rule-based parsing straightforward.

Tokenization can be implemented using basic Python string
operations.

Corpus membership can be checked through normalized string
comparison.

Accepted sentences can be further analyzed for word roles.

New words can be manually classified and stored in the word model.

New sentences can be added to the corpus.

The corpus can optionally be persisted using JSON.

The role-distribution analysis reflects the fixed structure of the
corpus.

⚠️ Limitations

This project is intentionally a basic NLP implementation and has several
limitations:

Fixed Grammar

The main parser assumes a five-word structure:

Determiner + Noun + Verb + Determiner + Noun

Position-Based Identification

Word roles are primarily identified using their position rather than
complete syntactic or semantic analysis.

Exact Corpus Matching

The system does not understand synonyms or paraphrases.

For example:

book a ticket
purchase a ticket

are treated as different sentences.

No Machine Learning

The system does not train a statistical or neural NLP model.

Simple Word Training

New word classification is based on user-provided categories rather
than an automatically trained POS tagger.

Limited Language Understanding

The system is designed specifically for the small ticket-booking
corpus and does not represent general English understanding.

🔮 Future Improvements

Possible improvements include:

Use a real POS tagger such as spaCy or NLTK.

Add stemming and lemmatization.

Support larger and more diverse datasets.

Add synonym and paraphrase handling.

Replace exact matching with semantic similarity.

Add a machine-learning-based sentence classifier.

Build a web interface for easier interaction.

Add intent detection such as booking, cancellation, payment, and
ticket confirmation.

Improve grammar parsing for sentences of different lengths.

Add database storage instead of a JSON file.

🎓 Academic Learning Outcomes

This mini project demonstrates practical understanding of:

Natural Language Processing

Text tokenization

Corpus creation

Word-role/POS identification

Rule-based parsing

Dictionaries and word models

Data normalization

Basic data analysis

JSON persistence

Python programming

👨‍💻 Author

Name: G Tharun
Course: CSE 306 --- Natural Language Processing
Project: Smart Ticket Booking --- Corpus-Based NLP Sentence Parser

📄 Project Information

Project Type: Academic Mini Project
Domain: Natural Language Processing
Approach: Rule-Based NLP
Language: Python
Environment: Jupyter Notebook

⭐ Conclusion

The Smart Ticket Booking --- Corpus-Based NLP Sentence Parser
demonstrates how basic NLP functionality can be implemented using simple
Python structures and rules.

The project covers the complete workflow of taking a sentence,
tokenizing it, checking it against a domain-specific corpus, identifying
word roles, adding new sentences, learning new word categories, and
storing the updated corpus.

Although the system is intentionally simple and does not use
machine-learning-based NLP, it provides a clear foundation for
understanding how more advanced NLP systems can be developed.
