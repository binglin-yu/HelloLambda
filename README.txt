Example codes for maintaining lambda via aws cli:

# create lambda
aws lambda  create-function \
--region eu-west-1 \
--function-name BYU-TEST-LAMDA \
--runtime java8 \
--role arn:aws:iam::015887481462:role/lambda_basic_execution \
--zip-file fileb:///Users/U8015921/NetBeansProjects/hello-lambda/target/hello-lambda-1.0-SNAPSHOT.jar \
--handler example.Hello::myHandler \
--profile default


#invoke to test
aws lambda invoke \
--invocation-type RequestResponse \
--function-name BYU-TEST-LAMDA \
--region eu-west-1 \
--payload '"byu"' \
--profile default \
outputfile.txt

#update codes
aws lambda update-function-code \
--function-name "arn:aws:lambda:eu-west-1:015887481462:function:BYU-TEST-LAMDA" \
--zip-file fileb:///Users/U8015921/NetBeansProjects/hello-lambda/target/hello-lambda-1.0-SNAPSHOT.jar

#another way to invoke
aws lambda invoke \
--invocation-type RequestResponse \
--function-name "arn:aws:lambda:eu-west-1:015887481462:function:BYU-TEST-LAMDA" \
--payload '"byu"' \
outputfile.txt

#delete lambda
aws lambda delete-function \
--function-name "arn:aws:lambda:eu-west-1:015887481462:function:BYU-TEST-LAMDA"

#list all funs
aws lambda list-functions

#get info of a lambda
aws lambda get-function --function-name "arn:aws:lambda:eu-west-1:015887481462:function:BYU-TEST-LAMDA"

