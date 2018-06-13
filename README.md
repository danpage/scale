# SCALE: Side-Channel Attack Lab. Exercises

<!--- -------------------------------------------------------------------- --->

## Concept

Alongside the implementation of cryptography in hardware *and* software, 
attacks on those implementations (plus associated countermeasures) form
a central challenge in
[cryptographic engineering](http://en.wikipedia.org/wiki/Cryptographic_engineering).
This topic is sometimes termed physical security, but, either way, it
contrasts sharply with
traditional [cryptanalysis](http://en.wikipedia.org/wiki/Cryptanalysis)
by targeting the concrete implementation (vs. the abstract design, i.e.,
the underlying theory) via techniques such as 
[side-channel attack](http://en.wikipedia.org/wiki/Side-channel_attack).
Beyond the obvious motivation, there are many position statements, e.g.,
see [1,2,3], that outline why this challenge is important.  Thus, from 
an educational perspective, the question is how to equip students with 
an appropriate, associated skill set?  

On one hand, it seems obvious a hands-on approach is preferable: this is
an applied topic so actually *doing* it (assuming a background in the 
underlying or related theory), e.g., via 
[Problem-Based Learning (PBL)](http://en.wikipedia.org/wiki/Problem-based_learning),
would be most effective.  Indeed, other initiatives have already used a
similar approach, e.g., see [4].
However, on the other hand, our experience is that some practical and/or
logistical challenges remain.  In particular, a PBL-based approach will
demand some "problems" and, potentially, infrastructure for students to 
use.  This facts act as a driver for the SCALE project: the goal is to 
provide a suite of material related to side-channel (and fault) attacks 
that is 

- low-cost   (i.e., has few if any barriers to use),
- accessible (i.e., offers a balanced, configurable difficulty level, between real-world and educationally focused examples),
- relevant   (e.g., addresses modern challenges with tangible value and impact),
- coherent   (e.g., well documented and supported), and
- effective  (i.e., elicits appropriate learning outcomes).

<!--- -------------------------------------------------------------------- --->

## Content

#### Prepare pre-requisites

Some content is stored using
[Git Large File Storage (LFS)](http://git-lfs.github.com/):
it makes sense to install this first, otherwise that content appears
as a set of pointers to data vs. the data itself.

#### Prepare     repository

Use

```
git clone http://www.github.com/danpage/scale.git
```

to clone the repository, then

```
cd scale ; export SCALE="${PWD}"
```

to fix the working directory.
Note that, either way, the associated path is denoted by 
`${SCALE}` 
from here on.  

#### Prepare     submodules

Over time, SCALE has evolved in different directions; the content is
therefore captured by several offshoots.  Each is motivated as above, 
but differ in terms of their focus and content:

- The `${SCALE}/sw`
  directory houses the
  [software-oriented offshoot](http://www.github.com/danpage/scale-sw):
  the goal is to provide a set of high-level,
  [CTF](http://en.wikipedia.org/wiki/Capture_the_flag#Computer_security)-like
  exercises that offer controlled, simulated environments in which to 
  learn about various attack techniques.
   
- The `${SCALE}/hw`
  directory houses the 
  [hardware-oriented offshoot](http://www.github.com/danpage/scale-hw):
  the goal is to provide a set of  low-level,
  concrete hardware platforms that are tailored toward learning about
  [side-channel attacks](http://en.wikipedia.org/wiki/Side-channel_attack)
  based on
  [power analysis](http://en.wikipedia.org/wiki/Power_analysis).
   
- The `${SCALE}/data` 
  directory houses the 
  [    data-oriented offshoot](http://www.github.com/danpage/scale-data):
  the goal is to provide some (pre-acquired) data sets, each relating
  to one of the platforms in the hardware-oriented offshoot but that 
  can be used without physical access to the associated hardware.
   
These offshoots are organised as
[submodules](http://www.git-scm.com/docs/git-submodule),
which allows their content to be selectively populated.  This can be
important: the size (and so also download time) of the data-oriented 
offshoot is significant, for example, and it will not be applicable 
in all contexts or to all users.  As such, *either*

1. populate *all*  content via

   ```
   git submodule update --init --recursive
   ```

   *or*

2. populate *some* content via
    

   ```
   git submodule update --init --recursive sw
   git submodule update --init --recursive hw
   git submodule update --init --recursive data
   ```
   
   selectively removing commands to reflect the content you need.

<!--- -------------------------------------------------------------------- --->

## FAQs

- **"I've found a bug/typo in or have suggestion/improvement for X"**
  I'm always interested in improving SCALE: let us know, or even better
  create and send a pull request, and I'll try to integrate the change
  (if/when appropriate) as soon as possible.

- **"I've used SCALE for X!"**
  If you want to make reference to 
  SCALE
  (e.g., in the acknowledgements of a paper or report), it'd be *really*
  helpful if you'd use the following standard BiBTeX entry

  ```
  @misc{scale,
    author = {D. Page},
    title  = {{SCALE}: {S}ide-{C}hannel {A}ttack {L}ab. {E}xercises},
    url    = {http://www.github.com/danpage/scale}
  }
  ```

  since this will maximise the cases where it's picked up by automated
  citation indexes.

- **"Don't you mean *implementation* attack, not *side-channel* attack?"**
  Yes: for sure the content covers a broader range of concepts than the
  strict definition of a side-channel (or information leakage) attack.
  Originally SCALE was motivated by the challenge of scaling a research
  lab. to suit teaching, and, however (in)accurate, it just stuck.  But
  IMPALE would have been a great acronym in hindsight ...

<!--- -------------------------------------------------------------------- --->

## TODOs

- In the long term, it seems sensible to
  harness various functionality offered by
  [GitHub](http://www.github.com),
  e.g., by

  - moving the (increasingly voluminous) content in various `README.md`
    into a more easily maintained
    [wiki](http://help.github.com/articles/about-github-wikis),
  - taking advantage of some form of
    [Continuous Integration (CI)](http://www.github.com/marketplace/category/continuous-integration),
    to automatically build and test elements of the project.

<!--- -------------------------------------------------------------------- --->

## References

1. S. Ravi, A. Raghunathan, P.C. Kocher, and S. Hattangady.
   [Security in embedded systems: design challenges](http://dl.acm.org/citation.cfm?doid=1015047.1015049).
   ACM Transactions on Embedded Computing Systems (TECS), 3(3), 461--491, 2004.

2. S. Ravi, P.C. Kocher, R.B. Lee, G. McGraw, and A. Raghunathan.
   [Security as a new dimension in embedded system design](http://dl.acm.org/citation.cfm?id=996771).
   Design Automation Conference (DAC), 753--760, 2004.

3. W. Burleson, O. Mutlu, and M. Tiwari.
   [Who is the major threat to tomorrow's security?  You, the hardware designer](http://dl.acm.org/citation.cfm?doid=2897937.2905022).
   Design Automation Conference (DAC), 16:1--16:5, 2016.

4. F. Bruguier, P. Benoit, L. Torres, and L. Bossuet.
   [Hardware security: From concept to application](http://ieeexplore.ieee.org/document/7496483/).
   European Workshop on Microelectronics Education (EWME), 2016.

<!--- -------------------------------------------------------------------- --->
