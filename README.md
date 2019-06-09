# andrew_ng-ML
Notes from Andrew's NG popular Machine Learning class from Stanford (Coursera)


## Tips
Add Octave to path:
* Get your octave's path (usually displayed on the top when running octave-cli i.e. ~$/usr/local/octave/3.8.0/bin/octave-3.8.0
* Edit ~/.bash_profile i.e. vi ~/.bash_profile
* add an "alias" to octave i.e. alias octave="/usr/local/octave/3.8.0/bin/octave-3.8.0"
* reload your changes i.e. source ~/.bash_profile

Now you can use octave from the CLI

Another issue I had is with GNUplot, (AquaTerm error) to solve it this worked for me:

* echo "setenv("GNUTERM","qt")" > ~/.octaverc 

Also there are some other interesting solutions here:
https://stackoverflow.com/questions/13786754/octave-gnuplot-aquaterm-error-set-terminal-aqua-enhanced-title-figure-1-unk


## Octave commands (unofficial transcript)

### Moving Data Around
A= [1 2; 3 4 ; 5 6;]  % creates 3x2 matrix

* **size(A)** % returns 3 2
* **size(A,1)** %returns 3
* **size(A,2)** %returns 2

you can use length as well (usually on vectores as returns the longer dimension)
* **v = [1 2 3 4]** % creates a vector
* **length(v)** % returns 4

* **pwd** % returns current working directory
* **ls** % ls on current directory (like "dir" on windows)
* **cd** % change directory (kind of cool you can access system directly from octave)

* **load featuresX.dat** % loads featuresX.dat
* **load priceY.dat** % loads priceY.dat

* **who** % returns variables in current scope
* **whos** % return variable in current scope plus size bytes and type (class)

If you want print data from one of the loaded files...
* **featuresX** % once loaded return the values

Create a vectory with info from a loaded file
* **v = priceY(1:10)**

Then you can save the value of v in disk
* **save hello.mat v;** % this will save the variable v and when you load it again v will be there
* **save hello.mat v -ascii;** % this will save the variable v in text
* **load hello.mat**


**A = [1 2; 3 4; 5 6]**
A = 
    1 2
    3 4
    5 6

So...

* **A(3, 2)** % returns 6
* **A(2,:)** % ":" means every element along that row or columng so will return 3 4
* **A(:,2)** % returns all the second column  
                                            2
                                            4
                                            6

Also you can use this notation to assign values
* **A(:,2) = [10; 11; 12;]** % will replace whatever is in second column

If you want to append a new column...
* **A = [A, [100; 101; 102]];** % this will append a new column 
                                                              1 2 100
                                                              3 4 101
                                                              5 6 102

one more "sofisticated" function i.e. get only first and last rows:
* **A([1 3],:)** % returns 
                          1 2
                          5 6

* **A(:)** % puts all elements of A into a single column vector

Concatenating matrix
**A = [1 2; 3 4; 5 6;]**
**B = [11 12; 13 14; 15 16;]**


* **C = [ A B]** %
or
* **C = [A, B]** %
                  1 2 11 12
                  3 4 13 14
                  5 6 15 16
 
* **C = [A; B]** %
                  1 2 
                  3 4 
                  5 6 
                  11 12
                  13 14
                  15 16

... as long as they match, otherwise you will get an error like this
*"error: vertical dimensions mismatch (3x3 vs 3x2)"*


### Computing on Data
Setting up some matrices
A = [1 2; 3 4; 5 6]
B = [11 12; 13 14; 15 16]
C = [1 1; 2 2]

* **A * C** % regular matrix multiplication
* **A .* B** % element wise multiplaction

This also applies for 
* **A .^ B**
* **A ./ B**

Lets define a new vector
**v = [1; 2; 3;]**

Some element wise functions
* **1 ./ v** % inverse of all elemnts of v
* **log(v)** % logarithm
* **exp(v)** % exponentital
* **abs(v)** % absolute value

Make al elements of v negative
* **-v** % same as -1 * v

* **v + ones(lenght(v),1)** % adding one to all elements of v

Simplier method is to:
* **v+1** % same as before

Now let's transpose a matrix:
* **A'** % transposes A
* **(A')'** % a transpose of a transpose, of course returns the original

Let's define another vector
a = [1 15 2 0.5]

* **val = max(a)** % as this is a vector will return the max value and assign it to val
val = 15
* **[val, ind] = max(a)** % ind will be the index wehre the max value is (in this case 2)

WARNING if you execute max to a matrix i.e. max(A) will return the column wise max

Comparisons
* **a < 3** % will return element wise comparison 
                                                  1 0 1 1
* **find(a < 3)** % will return the values of all that matches this condition

* **[r,c] = find(A >= 7)** % will return the position of the elements

* sum(a)
prod(a)
floor(a)
ceil(a)

To get the max of each column
A = 
    8 1 6
    3 5 7
    4 9 2
    
* **max(A,[],1)** % returns the max for each column
                                                  8 9 7
* **max(A,[],2)** % returns the max for each row
                                                  8 7 9

To get the maximum on a Matrix
* **max(max(A))**  % returns a scalar with the maximum

Or you can convert your matrix into a vector

* **max(A(:))**

Per column sum

* **sum(A,1)** 

Per row sum
* **sum(A,2)**

#### Bonus (geeky commands for fun)
* A = magic(9)
* sum(A, 1)
* sum(A, 2)

Construct identity matrix (eye function)
* eye(9)

* A .* eye(9)

* sum(sum( A .* eye(9) ))
* sum(sum( A .* flipupd(eye(9)) ))

A= magic(3)

* pinv(A)
* temp = pinv(A)
* temp * A





