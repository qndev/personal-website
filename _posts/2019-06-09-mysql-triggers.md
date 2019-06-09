---
title: "MySQL triggers"
published: true
comments: true
---

:blush: :smiley: :relaxed: :+1: :wave: :rose: :herb: :palm_tree: :leaves: :blossom: :cactus: :four_leaf_clover: :hibiscus: :evergreen_tree: :seedling: :bell: :gift: :turtle: :snowman: :zap: :notes: :sparkles: :heart: :foggy: :blue_heart: :v: :christmas_tree: :santa: :pushpin: :basketball: :golf: :books: :guitar: :tangerine: :corn: :eggplant: :tomato: :strawberry: :green_apple: :cherries: :lemon:

#### :pushpin: Các bảng trong CSDL

> Để có thể thực hành với triggers 
> trong sql ta tạo các bảng trong cơ sở dữ liệu
> với cấu trúc các cột và kiểu dữ liệu dưới đây.

:one: Bảng **Student**

```sql
CREATE TABLE `student` (
	`student_id` varchar(45) NOT NULL,
	`name` varchar(45) NOT NULL,
	`date_of_birth` date NOT NULL,
	`student_class`	varchar(45) NOT NULL,
	`edu_program` varchar(45) NOT NULL,
	`training_system` varchar(45) NOT NULL,
	`state`	varchar(45) NOT NULL,
	`year` varchar(45) NOT NULL,
	`department` varchar(45) NOT NULL,
	`email`	varchar(45) NOT NULL,
	`tuition_unit` float UNSIGNED NOT NULL,
	PRIMARY KEY(`student_id`)
);
```

:two: Bảng **Subject**

```sql
CREATE TABLE `subject` (
	`subject_id` varchar(45) NOT NULL,
	`subject_name` varchar(255) NOT NULL,
	`duration` varchar(45),
	`credit` int(11) NOT NULL,
	`tuition_credit` float NOT NULL,
	`weight` float NOT NULL,
	PRIMARY KEY(`subject_id`)
);
```

:three: Bảng **Class**

```sql
CREATE TABLE `class` (
	`id` int PRIMARY KEY AUTOINCREMENT,
	`class_id` varchar(255) NOT NULL,
	`class_subject_id` varchar(255) NOT NULL,
	`start_time` time NOT NULL,
	`end_time` time NOT NULL,
	`day` varchar(45) NOT NULL,
	`week` varchar(45) NOT NULL,
	`class_type` varchar(45) NOT NULL,
	`group_class` varchar(45) NOT NULL,
	`room` varchar(45) NOT NULL,
	`semester` varchar(45) NOT NULL,
	`total_registered` int NOT NULL,
	`max_register` int NOT NULL,
	`expiration_date` date,
	FOREIGN KEY(`class_subject_id`) REFERENCES `subject`(`subject_id`)
);
```

:four: Bảng **Register**

```sql
CREATE TABLE `register` (
	`id` int PRIMARY KEY AUTOINCREMENT,
	`student_id` varchar(45) NOT NULL,
	`register_class_id`	varchar(255) NOT NULL,
	FOREIGN KEY(`student_id`) REFERENCES `student`(`student_id`),
	FOREIGN KEY(`register_class_id`) REFERENCES `class`(`class_id`)
);
```

#### :pushpin: Triggers examples

:+1: Ex01: **BEFORE_INSERT** - Nếu thời gian đăng kí lớp đã hết sinh viên sẽ không đăng kí được lớp nữa, hoặc trong thời gian đăng kí mà số lượng sinh viên iuar lớp đó đã đầy, hoặc sinh viên đăng kí mã lớp không tông tại hoặc đã đăng kí rồi.

```sql
BEGIN
  IF((SELECT CURDATE()) > (SELECT date_to_exist FROM class WHERE NEW.register_class_id = class_id))
    THEN
      SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Đã hết thời gian đăng kí lớp!';
  END IF;

  IF((SELECT total_registered FROM class WHERE NEW.register_class_id = class_id) >= (SELECT max_register FROM class WHERE NEW.register_class_id = class_id))
    THEN
    SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Đã hết chỗ đăng kí lớp!';
    // RAISE (ABORT, 'message');
  END IF;

  IF EXISTS (SELECT student_id, register_class_id FROM register WHERE student_id = NEW.student_id AND register_class_id = NEW.register_class_id) THEN
    SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Bạn đã đăng kí mã lớp này rồi!';
  END IF;

  IF (NEW.register_class_id NOT IN (SELECT class_id FROM class)) THEN  //using WHEN END, RAISE message with SQLite
    SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Không tồn tại mã lớp đăng kí.';
  END IF;

END

```

:+1: Ex02: **AFTER_DELETE** - Sau khi một sinh viên xóa lớp học đã đăng kí thì số lượng sinh viên đăng kí lớp học đó sẽ giảm đi 1 (trong bảng class).

```sql
BEGIN
  UPDATE class SET max_register = total_registered - 1
  WHERE class.class_id = OLD.register_class_id;
END

```

:+1: Ex03: **BEFORE_DELETE_REGISTER** - Nếu hết thời gian đăng kí lớp học thì sinh viên sẽ không được quyền xóa đăng kí lớp học nữa.

```sql
BEGIN

  IF((SELECT CURDATE()) > (SELECT expiration_date FROM class WHERE OLD.register_class_id = class_id)) THEN
    SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Đã hết thời gian điều chỉnh đăng kí lớp!';
  END IF;

END
```

:+1: Ex04: **AFTER_INSERT_REGISTER** - Kiểm tra nếu sinh viên đăng kí quá 24 tín chỉ thì sẽ không được đăng kí thêm lớp học nữa, hoặc nếu chưa vượt quá số tín chỉ quy định nhưng lớp vừa đăng kí đã trùng thời gianơi học với lớp đã đăng kí rồi.

```sql
BEGIN
     DECLARE id_student_param VARCHAR(45);
     DECLARE class_id_param VARCHAR(45);
     SET id_student_param = NEW.student_id;
     SET class_id_param = NEW.register_class_id;
     
     UPDATE class SET total_registered = total_registered + 1
     WHERE class.class_id = class_id_param;
     
IF((SELECT SUM(credit)
       FROM subject, class, register
       WHERE subject.subject_id = class.class_subject_id
       AND register.register_class_id = class.class_id   GROUP BY student_id) > 24)
  THEN
    SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Bạn đã đăng kí quá số tín chỉ quy định!';
END IF; 

IF((SELECT  COUNT(overlap1.register_class_id)
FROM    register overlap1, register overlap2
WHERE   (overlap2.start_time BETWEEN overlap1.start_time AND overlap1.end_time
        OR overlap2.end_time BETWEEN overlap1.start_time AND overlap1.end_time)
        AND overlap1.register_class_id <> overlap2.register_class_id
        AND overlap1.day = overlap2.day
        AND overlap1.student_id = overlap2.student_id) > 0) THEN
SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Mã lớp đăng kí đã bị trùng thời gian học.';
END IF;

END;
```
