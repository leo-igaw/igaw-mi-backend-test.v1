# IGAWorks MI개발실 플랫폼개발팀 채용 테스트

## 환경설정

- 쿼리 테스트 페이지에 접속 <a href="http://sqlfiddle.com/" target="_blank">\[CLICK\]</a>
- 좌측 패널에 아래 스키마를 작성하여 테이블 생성

```mysql
-- 사용자 정보
CREATE TABLE IF NOT EXISTS `user` (
`id` varchar(20) NOT NULL,
`name` varchar(10) NOT NULL,
`email` varchar(100) NOT NULL,
`regist_dt` datetime NOT NULL,
PRIMARY KEY (`id`)
) DEFAULT CHARSET=utf8;

INSERT INTO `user` (`id`, `name`, `email`, `regist_dt`) VALUES
('Landy', '철수', 'Landy@igaworks.com', '2021-03-21 17:35:11'),
('Leo', '광수', 'Leo@igaworks.com', '2021-04-03 13:24:01'),
('Roy', '용수', 'Roy@igaworks.com', '2021-02-13 07:51:32'),
('Min', '영희', 'Min@igaworks.com', '2021-03-17 09:04:17'),
('Frank', '가온', 'Frank@igaworks.com', '2021-03-11 18:22:59'),
('Dennis', '나봄', 'Dennis@igaworks.com', '2021-04-23 09:14:14'),
('Donald', '다빈', 'Donald@igaworks.com', '2021-01-11 06:55:41'),
('Athur', '가람', 'Athur@igaworks.com', '2021-04-14 09:51:32'),
('Edward', '나예', 'Edward@igaworks.com', '2021-03-27 19:32:34'),
('Harry', '다나', 'Harry@igaworks.com', '2021-02-22 23:25:32'),
('Peter', '로운', 'Peter@igaworks.com', '2021-01-19 21:46:51'),
('Richard', '마리', 'Richard@igaworks.com', '2021-02-03 08:14:25'),
('George', '바다', 'George@igaworks.com', '2021-04-22 09:29:24'),
('Fred', '보담', 'Fred@igaworks.com', '2021-04-16 10:33:16'),
('Jim', '소담', 'Jim@igaworks.com', '2021-03-12 11:14:25'),
('Mary', '새론', 'Mary@igaworks.com', '2021-04-01 12:42:51'),
('Carrie', '소미', 'Carrie@igaworks.com', '2021-01-21 15:33:34'),
('Dorothy', '슬옹', 'Dorothy@igaworks.com', '2021-03-19 14:27:32'),
('Helen', '이든', 'Helen@igaworks.com', '2021-01-27 17:41:34'),
('Carol', '초롱', 'Carol@igaworks.com', '2021-01-23 16:36:54'),
('Betty', '하루', 'Betty@igaworks.com', '2021-04-21 17:14:23'),
('Anna', '진이', 'Anna@igaworks.com', '2021-04-15 19:03:14'),
('Clara', '하은', 'Clara@igaworks.com', '2021-01-17 21:34:43'),
('Grace', '한별', 'Grace@igaworks.com', '2021-02-06 18:07:00');

-- 권한 정보
CREATE TABLE IF NOT EXISTS `user_role` (
`role_id` int NOT NULL,
`role` varchar(20) NOT NULL,
PRIMARY KEY (`role_id`)
) DEFAULT CHARSET=utf8;

INSERT INTO `user_role` (`role_id`, `role`) VALUES
(1, 'ROLE_BOARD'),
(2, 'ROLE_CONFIG'),
(3, 'ROLE_DATA');

-- 사용자와 권한 관계 정보
CREATE TABLE IF NOT EXISTS `rel_user_role` (
`id` varchar(20) NOT NULL,
`role` varchar(20) NOT NULL,
PRIMARY KEY (`id`, `role`)
) DEFAULT CHARSET=utf8;

INSERT INTO `rel_user_role` (`id`, `role`) VALUES
('Landy', 1),
('Leo', 1),
('Roy', 3),
('Landy', 2),
('Min', 2),
('Leo', 3),
('Landy', 3);

-- 휴면 사용자 정보
CREATE TABLE IF NOT EXISTS `inactive_user` (
`id` varchar(20) NOT NULL,
`name` varchar(10) NOT NULL,
`email` varchar(100) NOT NULL,
PRIMARY KEY (`id`)
) DEFAULT CHARSET=utf8;
INSERT INTO `inactive_user` (`id`, `name`, `email`) VALUES
('Robin', '장수', 'robin@igaworks.com'),
('Julian', '충수', 'julian@igaworks.com');
```

- 우측 패널을 통해 쿼리를 작성하세요.

## 요구사항

1. Landy(user.id)의 권한(user_role.role)을 모두 조회하세요.
2. 사용자(user) 중 2개 이상의 권한을 가진 사용자의 사용자 정보(user)를 모두 조회하세요.
3. 사용자(user)와 휴면 사용자(inactive_user)의 총 카운트를 조회하세요.
4. 사용자(user) 시간대 순으로 몇 명이 가입하였는지 조회하세요.

###### ex)

   | HOUR | COUNT |
   | :----: | :-----: |
   |  0   |    0    |
   |  1   |    0    |
   |  2   |    0    |
   |  3   |    0    |
   |  4   |    0    |
   |  5   |    0    |
   |  6   |    0    |
   |  7   |    2    |
   |  8   |    3    |
   |  9   |    1    |
   |  10   |    2    |
   |  11   |    3    |
   |  12   |    0    |
   |  13   |    5    |
   |  14   |    2    |
   |  15   |    1    |
   |  16   |    4    |
   |  17   |    5    |
   |  18   |    1    |
   |  19   |    2    |
   |  20   |    0    |
   |  21   |    1    |
   |  22   |    0    |
   |  23   |    0    |

   
   
   