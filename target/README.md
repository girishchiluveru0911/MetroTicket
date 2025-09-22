Q2)
a)
mvn clean install -U
b)
mvn package -Dskiptest
c)
rm -rf .*war\.cache


Q3)
a)git branch -m Uifixes
b)git fetch --all main
c)git add BookingController.java
git commit -m "error"
git checkout main
git merge payment-module
<<>> BookingController.java<<<>>>

d)git branch -d booking-module
e)git commit -m "1"
git commit -m "2"
git commit -m "3"

docker build -t metro-booking-app:latest .





Q3)
b)
git fetch origin
c)
git add BookingController.java

d)
git branch booking-module hashcode

f)git revert hashcode

g)
git stash
git checkout main
git checkout -b hotfix-branch
git checkout payment-module
git stash pop
h)git checkout your-feature-branch
git fetch origin
git rebase origin/main
git checkout main
git merge your-feature-branch
git format-patch HEAD~2..HEAD --stdout > my_patches.patch


j)git push --force-with-lease origin a1b2c3d:main
git fetch origin
git reset --hard origin/main



docker build -t metro-booking-app:latest .



docker run -d --name metro-app -p 9090:8080 metro-booking-app:latest -d runs detached, -p host:container.


docker run -d --name metro-app-1 -p 8081:8080 metro-booking-app:latest
docker run -d --name metro-app-2 -p 8082:8080 metro-booking-app:latest


git status
git add . && git commit -m "WIP: save local work"   




















































1) Abstract (Summarize the problem)

An online grocery delivery system (like BigBasket) allows customers to browse grocery items, add them to a cart, place orders, and make secure payments.
 Store managers track inventory, 
while delivery agents fulfill orders and update delivery status. 
The system improves convenience, reduces in-store traffic, and ensures accurate stock management.

2) Functional Requirements (examples)

User registration, login, and profile management.

Browse/search grocery items by category or name.

Add/remove items from the cart and update quantities.

Secure online payments with multiple gateways.

Order tracking with live status updates.

Manager dashboard for inventory and price updates.

Delivery agent portal to manage assigned orders.

3) Non-Functional Requirements (examples)

Performance: Pages must load within 3 seconds under normal load.

Scalability: System must handle increased users during peak hours.

Security: Use HTTPS and encrypt sensitive data.

Reliability: 99.9% uptime SLA.

Usability: Mobile-friendly, simple UI/UX.

Maintainability: Modular code with proper documentation.

4) Users

Customers: Browse, order, and track groceries.

Store Managers/Admins: Manage stock, pricing, and categories.

Delivery Agents: Fulfill and update delivery orders.

Payment Gateway/Third-Party Services: Handle secure payments.

5) Use Case Diagram (Text Representation)
          +------------------+
          |      Customer    |
          +------------------+
           |   Browse Items
           |   Add to Cart
           v
+-------------------+            +------------------+
| Online Grocery    |<---------->| Payment Gateway  |
| Delivery System   |            +------------------+
+-------------------+<---------->+ Delivery Agent   |
           ^                      +------------------+
           |Manage Inventory
           |
    +------------------+
    | Store Manager    |
    +------------------+

✅ Q2. Metro Booking System – Maven (30 Marks)
1) Resolve dependencies using pom.xml

In Eclipse: Right-click project → Maven → Update Project.

Or run:

mvn clean install

2) Build the project to generate WAR/JAR
mvn package

3) Verify artifact in target/ folder

Check the target directory for:

MetroBookingSystem-1.0-SNAPSHOT.war


or

MetroBookingSystem-1.0-SNAPSHOT.jar

4) Scenario-Based Questions (5 × 1 = 5 Marks)

a) Force update of dependencies:

mvn clean install -U


b) Skip tests for faster deployment:

mvn package -DskipTests


c) Configure different DB settings for dev/prod:
Use Maven profiles in pom.xml and activate:

mvn package -Pdev
mvn package -Pprod


d) Clear cached dependencies:

rm -rf ~/.m2/repository/<dependency>
mvn clean install -U


e) Fix missing compiler plugin: Add to pom.xml:

<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <version>3.8.1</version>
      <configuration>
        <source>1.8</source>
        <target>1.8</target>
      </configuration>
    </plugin>
  </plugins>
</build>


Then run:

mvn clean install -U

✅ Q3. Working with VCS Git and GitHub (30 Marks)
1) Initialize a Git repository and add project files (5 Marks)
git init
git add .
git commit -m "Initial commit"

2) Set Git global config and push Maven project to GitHub (5 Marks)
git config --global user.name "YourName"
git config --global user.email "your@email.com"
git remote add origin https://github.com/YourUsername/RepoName.git
git branch -M main
git push -u origin main

3) Solve Git scenario-based questions (10 × 2 = 20 Marks)

Scenario: While working in dev.jsp, you made UI fixes but mistakenly committed them on the main branch instead of ui-fixes. How do you move that commit?

✅ Steps to fix:

Create (or switch to) the correct branch ui-fixes:

git branch ui-fixes
git checkout ui-fixes


Move the latest commit from main to ui-fixes:

git cherry-pick <commit_hash>


(Find commit hash using git log.)

Go back to main and remove the incorrect commit:

git checkout main
git reset --hard HEAD~1


(Removes the commit from main while preserving it on ui-fixes.)

Push the updated branches:

git push origin main --force
git push origin ui-fixes

📋 Final Overview Table
Q#	Task	Key Commands / Points
Q1	Abstract, Functional/Non-Functional, Users, Use Case	Summarized above.
Q2	Maven build + scenarios	mvn clean install, mvn package, profiles, clear cache, fix plugins
Q3	Git/GitHub tasks + scenario fix	git init, git config, git push, cherry-pick, reset --hard

These answers cover all parts of Q1, Q2, and Q3 completely and concisely for your lab internal exam.
