# CPAN-228 Lab 4 – FitSquad Hub

## Changes made

This project has been updated for the WorkoutLog custom-query, sorting, and pagination requirements.

### Java files
- `repository/WorkoutLogRepository.java`
  - Added the athlete-name derived query.
  - Added the minimum-calories derived query.
  - Added the highest-calorie JPQL query.
  - Added the intensity and minimum-duration JPQL query.
- `service/WorkoutLogService.java`
  - Added pageable `getLogs` and wrappers for all four custom repository methods.
- `controller/WorkoutLogController.java`
  - Added page, size, sort, direction, search, and filterType request parameters.
  - Added the five requested filter routes.
  - Added the pagination and sorting values to the Thymeleaf model.

### Thymeleaf
- `src/main/resources/templates/workout-logs.html`
  - Added the search/filter form.
  - Added sortable Athlete, Date, Duration, Calories, and Intensity headers.
  - Added First, Previous, numbered, Next, and Last pagination links.
  - Pagination and sorting links preserve the current filters and page size.

## Run on Windows

Open a terminal in the project root folder and run:

```powershell
.\mvnw.cmd spring-boot:run
```

Then open:

- Workout Logs: http://localhost:8080/workout-logs
- Challenges reference: http://localhost:8080/challenges
- Log a workout: http://localhost:8080/log-workout
- H2 Console: http://localhost:8080/h2-console

H2 JDBC URL: `jdbc:h2:mem:fitsquadhub`  
Username: `sa`  
Password: leave blank

## Run automated tests

```powershell
.\mvnw.cmd test
```

## Testing the filters

The supplied `data.sql` seeds eight workout logs. Try these:

1. Athlete Name: choose **By Athlete Name**, enter `Alex`, then Search.
2. Minimum Calories: choose **By Min Calories Burned**, enter `400`, then Search.
3. Highest Calories: choose **Highest Calorie Burn - JPQL**, then Search.
4. Intensity and Duration: choose **By Intensity & Min 25m Duration - JPQL**, enter `High`, then Search.
5. Click Athlete, Date, Duration, Calories, or Intensity in the table header to toggle ascending/descending sorting.
6. If there are enough matching records, use the pagination controls.

## Important verification note

The project files have been updated, but automated Maven execution must still be completed on your computer. In the preparation environment, Maven could not be downloaded because access to Maven Central was unavailable. Do not treat the application as fully tested until `spring-boot:run` and `test` have completed successfully on your computer.
