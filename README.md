# IPC-POSIX-Producer
#include<stdio.h>
#include<stlib.h>
#include<string.h>
#include<fcntl.h>
#include<sys/shm.h>
#include<sys/start.h>
int main()
{
const intint SIZE 4096;
const char *name="OS";
const char *message_0="HELLO";
const char *message_1="world!";
int shm_fd;
void *ptr;
shm_fd=shm_open(name , O_CREAT | O_RDRW , 0666);
ftruncate(shm_fd, SIZE);
ptr=mmap(0, SIZE, PROT_WRITE, MAP_SHARED, shm_fd, 0);
sprintf(ptr, "%s", message_0);
ptr +=strlen(message_0);
sprintf(ptr, "%s", message_1);
ptr +=strlen(message_1);
return 0;
}
