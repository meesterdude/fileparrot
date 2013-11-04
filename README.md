# FileParrot

FileParrot is a simple tool to help you capture data thats relevant to you. Use it to log your workouts, as a journal, or something else entirely.

## Examples
Some example files created by FileParrot

### workout log

```
| Miles         | temp   | shoes |
| ------------- |:------:| -----:|
| 12 miles      | 79º    | red   |
| 3 miles       | 56º    |  red  |
| 6 miles       | 66º    |  blue |
```
### Journal

```
11/03/2013 @ 06:27AM: woke up
11/03/2013 @ 04:46AM: breakfast
11/03/2013 @ 05:00AM: Start workout
```
### litter box

```
11/03/2013 @ 06:27AM
11/04/2013 @ 07:46AM
11/05/2013 @ 09:10AM
```

### Report

```
I walked 19 miles today, which is GOOD. Time taken was 12 minutes. (1.58 a minute)
The weather was fair. I would describe the day as warm, but quiet.
---
I walked 5 miles today, which is OK. Time taken was 5 minutes. (1 a minute)
The weather was hot. I would describe the day as boiling and oh my god my eyes.
---
```
### Shopping List

```
1. eggs
2. bacon
3. apples
```
### CSV manipulation

```
Time,Distance_from_previous
11/03/2013 @ 06:27AM,0
11/03/2013 @ 06:28AM,1
11/03/2013 @ 06:33AM,5
```

## Installation
The following command must be run exactly as typed in order to install. WARNING: IF YOU MAKE A TYPO THE INSTALLATION WONT WORK AND YOUR COMPUTER MAY BECOME WINDOWS.

```
gem install fileparrot
```
Then, optionally, append something like this to your bash_profile to make entry easier

```
alias fp='fileparrot -d ~/tracking/templates/ -D ~/tracking/output/ -n'
```

## Features

### Templates
A template is a file that gets executed and then created or added elsewhere. Here's a template that asks your mood and provides a timestamp.

```
<%% happy = ask("whats your mood?", ['happy','mad','silly','drunk','awesome']) %%>
<%%= "|#{happy}|#{timestamp} |" %%>

```

The parser uses a custom synax for ERB. The two methods shown in the example above, `timestamp` and `ask` are provided as helpers; but you can use any ruby you want in there.

the previous file, when ran through, outputs this:

```
#### FileParrot ####
#### 2013 Russell Jennings ####
whats your mood?
1) happy
2) mad
3) silly
4) drunk
5) awesome
1,4
The following was appended to: /Users/ruru64/wiki/code/dest//output.md

|happy, drunk|11/04/2013 @ 04:02PM |
All done!
```

and the file looks like this

```
|drunk|11/01/2013 @ 03:39PM |
|sad, drunk|11/02/2013 @ 06:02PM |
|happy, drunk|11/03/2013 @ 04:27AM |
```

### Helper methods

#### ask
Takes two parameters: the question to ask, and an optional array of values. If the array is passed in, those options can be multi-selected from a list.

#### timestamp
outputs a friendly timestamp

#### options
any option passed in through the command line will be available through this hash.

### Parameters
The parameters taken are as follows:

```
Usage: listparrot [options]
    -d, --source_dir DIR             Source dir (required)
    -n, --source_name NAME           Source name (required)
    -D, --destination_dir DIR        Destination Dir (required)
    -N, --destination_name NAME      Destination name (defaults to the name of source_name)
    -a, --no_append                  create or overwrite instead of append
    -x, --no_parse                   Do not parse file for ERB (<%% %%> parsed by default)
    -h, --help                       Show this message
```

It is recommended to preset some of these values by aliasing the method. See the install section for details.

### Automagic logging
If you just want to track the occurrence of something, you don't need to create a template. Just pass in the name as usual, and if a source file can't be found, it'll just append a time stamp to a destination file of that name.

```
$ fp litter_box
#### FileParrot ####
#### 2013 Russell Jennings ####
The following was appended to: /Users/me/tracking/output/cleaned_litterbox
11/04/2013 @ 04:20PM

All done!
```

## License
MIT

## Future ideas
- running edits to files (merge the template and output file into same file)
- native read in CSV and spit out manipulation