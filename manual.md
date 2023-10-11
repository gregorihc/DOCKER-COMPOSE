### Generation and coverage
dotnet sonarscanner begin /k:"backen_coverage" /d:sonar.host.url="http://172.16.140.135:9000"  /d:sonar.login="bc448f52d6db3f00f656dba75c5e56954ec932b6" /d:sonar.coverageReportPaths=".\sonarqubecoverage\SonarQube.xml"
dotnet build
dotnet test --no-build --collect:"XPlat Code Coverage"
reportgenerator "-reports:*\TestResults\*\coverage.cobertura.xml" "-targetdir:sonarqubecoverage" "-reporttypes:SonarQube"
dotnet sonarscanner end /d:sonar.login="099f472869743ccf4b20fda6c682ffc9a5996b39"

Generacion de Reporte de sonarqub
java -jar sonar-cnes-report-4.1.2.jar -t a55cc6fe034bda4f9f67130a48ede1dd8e013053 -s http://172.16.140.135:9000 -p intercom_backend_julio -r ./intercom_backend_julio.docx

install:
dotnet tool install --global dotnet-sonarscanner
dotnet tool update dotnet-reportgenerator-globaltool -g

