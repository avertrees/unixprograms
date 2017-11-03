#!/usr/bin/env  perl
# written by Alessandra Vertrees
# October 29, 2017
# Description: A program that randomly generates math questions


$^W = 1;     # turn on warnings
use strict;  # behave!


# display the startup message
print "Welcome to the mathq program.\n";
print "Use \"q\" or \"Q\" if you wish to quit the program. \n";

# variables
my $user_wants_to_quit = 0;
# counter variables
my $total = 0;
my $correct = 0;
my $incorrect = 0;
my $pct = 0;

# LOOP until the user wants to quit
until ($user_wants_to_quit) {

    # GENERATE A RANDOM MATH QUESTION AND SOLUTION=
    # set first_num to a random integer in 0..9
    my $first_num  = int(rand(10));

    # set second_num to a random integer in 0..9
    my $second_num = int(rand(10));

    my $question;
    my $solution;

    # pick a random integer from 0 to 3 and use it to choose operation
    my $operator = int(rand(4));
    if ( $operator == 1 ) {
        # <<CREATE MULT QUESTION AND SOLUTION>>
        $solution = $first_num * $second_num;
        $question = "$first_num x $second_num = ";
    } elsif  ( $operator == 2 ) {
        # <<CREATE DIVISION QUESTION AND SOLUTION>>
        #If divisor is 0, change the oporator
        if ( $second_num == 0 ) {
                my @array = ('0', '1', '3');
                $operator = $array[rand @array];
        } else {
        $solution = $first_num * $second_num;
        #swap values
        ($solution, $first_num) = ($first_num, $solution);
        $question = "$first_num / $second_num = ";
        }
    } elsif ( $operator == 3 ) {
        # <<CREATE ADDITION QUESTION AND SOLUTION>>
        $solution = $first_num + $second_num;
        $question = "$first_num + $second_num = ";
    } else {
        # <<CREATE SUBTRACTION QUESTION AND SOLUTION>>
        $solution = $first_num + $second_num;
        #swap values. #if solution and first_num are swapped, $first_num will never equal 0
        #unless both $first_num and $second_num both equal 0. Either way, $solution will never be negative
        ($solution, $first_num) = ($first_num, $solution);
        $question = "$first_num - $second_num = ";
            }

    # <<DISPLAY QUESTION AND GET VALID RESPONSE>>=
    my $response;
    my $response_is_valid = 0; # set to FALSE
    until ( $response_is_valid ) {
        print "$question?\n> ";  # display question
        $response = <STDIN>;
        chomp($response);
        # <<CHECK IF RESPONSE IS VALID>>=
        if ( $response =~ m/^[0-9]+$/ or $response =~ m/^[Qq]/) {
            $response_is_valid  = 1;
        }
    }

    # <<CHECK CORRECTNESS OF USER'S RESPONSE>>
    if ( $response =~ m/^[Qq]/ ) {
        $user_wants_to_quit = 1;
    }
    else {
        #COUNT if response is correct increase value of $correct, if it is incorrect increase value of $incorrect 
        if ( $response == $solution ){
            print "Correct!\n";
           } else {
            print "Incorrect: $question $solution \n";
            $incorrect == ++$incorrect;
        }
        $total = $correct + $incorrect;
        # pct correct
        $pct = int(( $correct/$total ) * 100);
    }
}
# display the exit message
print "You answered $correct out of $total questions correctly, or $pct\%  correctly. \n";
print "Thank you for playing mathq.\n";
