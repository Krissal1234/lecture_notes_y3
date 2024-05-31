
A fault model for web apps

a transaction between a web user and a web server has three main components:

- the server computer 
- the client computer
- the network connecting them


In software testing of web app we must gather all the information we can even by attacking it.
We must attack comments embeddeed in html source, sensitive information in the html source, server side error messages and HTTP responses and application error messages

Comments can easily reveal insights about our code
- An attacker has access to our html code. Finding comments can be like a gold nugget, when writing html+inline php, put comments in your php code as the attacker will not view these


### Info in source code
- Info in source code might divulge:
	- secrets like database names, user logins and passwords
- Web crawlers like wget or BlackWidow can map out the pages of an app, but unles the app has 1000s of pages, its better to do this manually and this will make you a more efficient web tester

#### Slide 1: Initial Navigation

- **Action**: Begin at the app's start page.
- **Procedure**: Click every link to subsequent pages.
- **Task**: Document which pages can be reached.
- **Goal**: Ensure every page is visited.

#### Slide 2: Source Code Inspection

- **Action**: View the homepage source code.
- **Check for Comments**: Look for PHP, Perl, ASP, etc., comments.
- **Risk**: Comments should not appear in the HTML stream but might due to misplaced tags or improper commenting.
- **Example**: ColdFusion comments (`<!-- ... --->`) can reveal information if not properly formatted (`<!-- ... -->`).

#### Slide 3: Manual and Automated Comment Search

- **Issue**: Old code fragments in comments can expose information.
- **Manual Sifting**: Review comments manually.
- **Automated Tools**: Use tools like `grep` (available on *NIX and Windows via Cygwin or MinGW) for string pattern search.
- **Example Tool**: The Regulator for creating search regular expressions.

#### Slide 4: Error Handling Information Disclosure

- **Issue**: Error pages displaying code details.
- **Example**: Database connection errors showing code tags, table names, database names.
- **Risk**: Provides valuable information to attackers.

#### Slide 5: Application Crashes

- **Environment Examples**: ColdFusion, Java Servlets.
- **Issue**: Crashing the app via syntax error or unhandled exception.
- **Result**: Server responds with a function trace and code snippet.
- **Risk**: Information disclosure of critical details.

#### Slide 6: Defensive Measures

- **Action**: Handle errors without disclosing details.
- **PHP Example**: Disable error messages from being echoed.
- **Recommendation**: Save error messages in a log file for developers.
- **Goal**: Prevent attackers from gaining insights through error messages.

