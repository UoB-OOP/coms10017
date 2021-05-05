Assessment
==========

Projects will be marked considering your team submission (code and report) and your project
presentation in unity.

You must submit code produced by you and your partner only; plagiarism of any kind (e.g. submission
of code not produced directly by your team) will be dealt with under university regulations. If any
third party library is used it needs to be clearly cited in your code. You must also flag any use of
third party library in your implementation before your presentation.

Your individual understanding of your implementation and principles of object orientation in
general, as well as the quality and clarity of the work conducted and depth of knowledge shown in
your presentation are considered for marking. A brief assessment guideline is provided below, also
giving details on the report. You can pass this coursework by submitting code that passes the tests,
and showing a good understanding of the code written and principles used. Note, that there are
limited and diminishing returns when implementing your AI solution, and we advise you to finish all
other parts first and make sure you are confident about the key principles of object-orientation and
Java before spending time on an AI solution.

Make sure you submit at least 1 hour early to avoid upload problems. Any submission after the
deadline will result in a loss of marks. Each team member has to upload an identical copy of the
submission zip file containing all of the work of the team. After the submission, each team will
present their work, where a time table for presentations will be published on the unit website. Both
team members must be present for the presentation. During the presentation we may run and discuss
your submitted program. You may run it on your own devices or the lab machines - you have to make
sure that your submitted program runs without problems. We will ask you questions about your work
and general principles of object-orientation and Java, and you will be able to showcase your
knowledge and the merits of your project. All team members should understand all code developed in
detail.

Submission
==========
You should submit before the deadline:

1. A brief **PDF** report (we expect this to be at least 1 page as a summary of what has been done,
   and 2 pages maximum reflecting on achievements. A strict maximum of 3 pages applies where the report should include some brief critical reflection on the merits and
   limitations of your work). **The file must be named report.pdf**
2. A compiling, building and running version of Scotland Yard including all source code to
   BlackBoard before the deadline in form of one single zip file called `sy.zip`. Your sub-projects
   `cw-model` and `cw-ai` must be in two different top level subfolders called `cw-model`
   and `cw-ai` within the zip file. Also include your `report.pdf` at the top level, next to `cw-model` and `cw-ai`.

Concretely, submit the following:

**Update: only submit 1 (one) file, `sy.zip` to BB, when you extract it, it should have the following structure:**

```
Submission 1:
 - sy.zip
   ├── report.pdf  # your PDF report
   ├── cw-model/   # root of the cw-model project, where running `mvnw clean test` will show all tests passing
   │    ├── mvnw
   │    ├── mvnw.cmd
   │    ├── pom.xml
   │    ├── src/
   │    └──  ...   # (any other file required for the project to compile can be in this directory)
   └── cw-ai/      # root of the cw-ai project, where running `mvnw clean compile exec:java` will run the project
        ├── mvnw
        ├── mvnw.cmd
        ├── pom.xml
        ├── src/
        └──  ...   # (any other file required for the project to compile can be in this directory)
```

**Failure to adhere to these requirements will result in loss of marks; we can't mark reports that
are not in PDF format or source files that are not compressed in zip format.**

Make sure you run the following of each of your sub-projects before submitting to remove compiled
binaries:

```shell
> mvnw clean
```

In any case, check that the version of your project resulting from unzipping your submission file
contains all source code and resources you created, that it compiles, passes all tests, and allows
you to run your game without the need for any other file outside your submission. The report does
not have to cover all things implemented in detail, but should be seen as an overview of the work
judged in conjunction with code and presentation - teams can use it during the presentation as an
aid. The report should be concise, clear and to the point.


Marking Guideline
=================

<table width="701" border="1">
  <tbody><tr>
    <td width="199"><strong>KEY TOPIC</strong></td>
    <td width="280"><strong>REQUIREMENTS</strong></td>
    <td width="142"><strong>MARK</strong></td>
  </tr>
  <tr>
    <td>Passing vast majority of Tests of CW-MODEL</td>
    <td valign="bottom"><p>- compiling project code<br/>
        - appropriate use of basic OO concepts including classes and objects, attributes and methods, encapsulation etc. <br/>
        - use of the test suite<br/>
        - minimal code documentation<br/>
        - basic understanding of key OO concepts<br/>
        - basic report<br/>
    </p>       </td>
    <td valign="bottom">up to 40%</td>
  </tr>  <tr>
    <td>Passing all Tests of CW-MODEL</td>
    <td valign="bottom"><p>In addition to the above:<br/>
        - good use of OO concepts including overloading/overriding, immutables and generics<br/>
        - good code documentation<br/>
        - well readable OO-style code<br/>
        - concise report<br/>
        - evidence of positive individual contributions<br/>
    </p>       </td>
    <td valign="bottom">up to 50%</td>
  </tr>
  <tr>
    <td>Good understanding and use of OO Concepts</td>
    <td valign="bottom"><p>In addition to the above:<br/>
        - good implementation/understanding of observer pattern<br/>
        - good use of wide variety of OO concepts including polymorphism, abstraction etc.<br/>
        - good understanding of all basic OO concepts<br/>
        - well structured OO-style, DRY code<br/>
    </p>       </td>
    <td valign="bottom">up to 55%</td>
  </tr>
  <tr>
    <td>Basic MrX Board Scoring Function</td>
    <td valign="bottom"><p>In addition to the above:<br/>
        - simple MrX scoring function for generating a basic score from a Board<br/>
        - good implementation/understanding of dynamic dispatch and visitor pattern<br/>
        - good understanding of wide variety of OO concepts<br/>
        - well written report<br/>
        - evidence of productive individual contributions<br/>
    </p>       </td>
    <td valign="bottom">up to 60%</td>
  </tr>
  <tr>
    <td>Very Good Code Structure and Good Scoring Function</td>
    <td valign="bottom"><p>In addition to the above:<br/>
        - well-tested and effective MrX scoring function<br/>
        - very good understanding and use of most OO concepts and some good understanding of basic design patterns<br/>
        - very well documented code that is widely following very good coding practice<br/>
        - very well written report<br/>
    </p>       </td>
    <td valign="bottom">up to 65%</td>
  </tr>
  <tr>
    <td>Excellent Code, Report and Understanding + Distance-based Look-Ahead-One AI</td>
    <td valign="bottom"><p>In addition to the above:<br/>
        - an AI that can pick the next best move for MrX based on a good scoring function that considers distances to the detectives<br/>
        - excellent understanding of OO concepts and good understanding of variety of design patterns<br/>
        - very good practical OO use, ability to link concepts with development/coding choices<br/>
        - excellently written report with critical reflection<br/>
        - individual contributions have aspects of excellence<br/>
    </p>       </td>
    <td valign="bottom">up to 70%</td>
  </tr>
  <tr>
    <td>MiniMax-like Implementation + Excellent, Critical Understanding of OO and Design Patterns</td>
    <td valign="bottom"><p>In addition to the above:<br/>
        - an AI that can pick the best move for MrX based on a Game Tree and the MiniMax Algorithm (or similarly complex, formal framework)<br/>
        - appropriate and measured use of design patterns, critical understanding of OO principles<br/>
        - work, presentation, report and extensions all show excellent, critical understanding of both OO and design patterns<br/>
        - evidence of excellence in individual contributions<br/>
    </p>       </td>
    <td valign="bottom">up to 75%</td>
  </tr>
  <tr>
    <td>Excellence and Critical OO Thinking beyond Course Content + Optimised AI</td>
    <td valign="bottom"><p>In addition to the above:<br/>
        - research and implementation of algorithms or features in complexity beyond MiniMax that allow for a more dynamic, effective and efficient AI<br/>
        - work, presentation and extensions all show an excellent and critical understanding of OO and design patterns beyond lecture materials<br/>
        - marks at and above 80 are reserved for cases, where work, presentation and report all show mastery of the subject<br/>
        - evidence of excellence and mastery of the subject in individual contributions<br/>
    </p>       </td>
    <td valign="bottom">up to 85%</td>
  </tr>
  <tr>
    <td>Outstanding Work</td>
    <td valign="bottom"><p>In addition to the above:<br/>
      - outstanding extensions and mastery of advanced methods in all aspects showing truly deep understanding and novel ideas<br/>
      - product built is of such quality that it is publishable 'as is' under appropriate conditions<br/>
      - outstanding knowledge far beyond the unit apparent in all work, presentation and report<br/>
      - exceptional command of theory and techniques all showing deep critical analysis and reflection<br/>
      - evidence of outstanding individual contributions<br/> 
    </p>       </td>
    <td valign="bottom">up to 100%</td>
  </tr>
</tbody></table>
