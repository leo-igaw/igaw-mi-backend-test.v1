# IGAWorks MI개발실 플랫폼개발팀 채용 테스트

## 환경설정

- 브라우저에서 http://sqlfiddle.com/ 에 접속
- 좌측 패널에 아래 스키마를 작성하여 테이블 생성

```mysql
-- 사용자 정보
CREATE TABLE IF NOT EXISTS `user` (
  `id` varchar(20) NOT NULL,
  `name` varchar(10) NOT NULL,
  `email` varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
) DEFAULT CHARSET=utf8;

INSERT INTO `user` (`id`, `name`, `email`) VALUES
  ('landy', '철수', 'landy@igaworks.com'),
  ('leo', '광수', 'leo@igaworks.com'),
  ('roy', '용수', 'roy@igaworks.com'),
  ('min', '영희', 'min@igaworks.com');

-- 권한 정보
CREATE TABLE IF NOT EXISTS `user_role` (
  `role` varchar(20) NOT NULL,
  `regist_dt` datetime NOT NULL,
  PRIMARY KEY (`role`)
) DEFAULT CHARSET=utf8;

INSERT INTO `user_role` (`role`, `regist_dt`) VALUES
  ('ROLE_BOARD', now()),
  ('ROLE_CONFIG', now()),
  ('ROLE_DATA', now());

-- 사용자와 권한 관계 정보
CREATE TABLE IF NOT EXISTS `rel_user_role` (
  `id` varchar(20) NOT NULL,
  `role` varchar(20) NOT NULL,
  `expire_dt` datetime NOT NULL,
  PRIMARY KEY (`id`, `role`)
) DEFAULT CHARSET=utf8;

INSERT INTO `rel_user_role` (`id`, `role`, `expire_dt`) VALUES
  ('landy', 'ROLE_BOARD', now()),
  ('leo', 'ROLE_BOARD', now()),
  ('roy', 'ROLE_DATA', now()),
  ('landy', 'ROLE_CONFIG', now()),
  ('min', 'ROLE_CONFIG', now()),
  ('leo', 'ROLE_DATA', now()),
  ('landy', 'ROLE_DATA', now());

-- 휴면 사용자 정보
CREATE TABLE IF NOT EXISTS `inactive_user` (
  `id` varchar(20) NOT NULL,
  `name` varchar(10) NOT NULL,
  `email` varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
) DEFAULT CHARSET=utf8;
INSERT INTO `inactive_user` (`id`, `name`, `email`) VALUES
  ('robin', '장수', 'robin@igaworks.com'),
  ('julian', '충수', 'julian@igaworks.com');
```

- 우측 패널을 통해 쿼리를 작성하세요.

## 요구사항

1. landy의 권한을 모두 조회하세요.
2. 사용자 중 2개 이상의 권한을 가진 사용자의 사용자 정보를 모두 조회하세요.
3. 사용자와 휴면 사용자의 총 카운트를 조회하세요.