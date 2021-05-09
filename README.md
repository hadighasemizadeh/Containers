Descriptions:

+GTest:
	Desc: GoogleTest container for cpp dev
	Build CMD: build -t ubuntu2004/gtest:v1.0.0 .
	Run CMD: docker run -ti --name=ubuntu-gtest -p 9090:8080 <IMAGE_ID>



Note:

- Windows users add "winpty"in the beggining of their commands if they receive  "the input device is not a TTY.  If you are using mintty, try prefixing the command with 'winpty'" error.

- After you built your container, you can get your IMAGE_ID with the following command: docker images 