environment {
 String result=’0.0.0';
 }
 stage(‘preparation’){
 steps {
 echo “Build Preparation” 
checkout scm } }
stage(‘Auto tagging’)
{ 
steps {
 script {
 sh “”” 
version=\$(git describe — tags `git rev-list — tags — max-count=1`)
#Version to get the latest tag 
A=”\$(echo \$version|cut -d ‘.’ -f1)”
B=”\$(echo \$version|cut -d ‘.’ -f2)”
C=”\$(echo \$version|cut -d ‘.’ -f3)”
 if [ \$C -gt 8 ]
 then 
if [ \$B -gt 8 ]
 then
 A=\$((A+1))
 B=0 C=0 
else
B=\$((B+1))
 C=0
 fi
 else
 C=\$((C+1))
 fi
echo “A[\$A.\$B.\$C]”>outFile “””
nextVersion = readFile ‘outFile’ 
echo “we will tag ‘${nextVersion}’” 
result =nextVersion.substring(nextVersion.indexOf(“[“)+1,nextVersion.indexOf(“]”);
echo “we will tag ‘${result}’”
withCredentials([usernamePassword(credentialsId: ‘github-token_jenkins’, passwordVariable: ‘password_name’, usernameVariable: ‘git_username’)]) { 
sh “”” 
 curl — data ‘{
“tag_name”: “${result}”,
 “target_commitish”: “release”,
 “name”: “${result}”,
 “body”: “Release of version ${result}”,
 “draft”: false, “prerelease”: false}’ \ https://github.com/api/v3/repos/project/repo/releases?access_token=${password_name}
}						 
