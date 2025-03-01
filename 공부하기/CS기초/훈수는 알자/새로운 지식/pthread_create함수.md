```
기본형
int pthread_create(pthread_t * restrict thread,
		const pthread_attr_t *restrict attr,
		void *(*start_routine)(void *),
		void *restrict arg);
```

```
매개변수
pthread_t *restrict thread
	스레드의 식별자
    
const pthread_attr_t *restrict attr
	설정할 스레드 속성정보(NULL 입력시 기본설정 적용)
    
void *(*start_routine)(void *)
	스레드가 실행할 함수
    
void *restrict arg
	스레드가 실행할 함수에 들어갈 인자
```
1. 함수 호출
pthread_create() 함수 호출 시 새 스레드가 생성되고, 생성된 스레드는 start_routine(arg)를 실행합니다.
```
종료 방법
- pthread_exit() 호출
- start_routine() 수행 후 return
- pthread_cancel() 호출
```
2. return
 -성공시 0을 반환하고 스레드의 식별자를 thread_t에 담음  
-오류 발생시 오류 번호를 반환하고 thread_t를 정의하지 않음
1. 에러
```
EAGAIN	리소스가 부족하여 다른 스레드를 만들 수 없습니다.
EINVAL	attr의 설정이 잘못되었습니다.
	스레드 수가 제한을 넘었습니다. 
EPERM	attr에 지정된 스케줄링 정책 및 매개 변수를 
       설정할 수 있는 권한이 없습니다.
```

