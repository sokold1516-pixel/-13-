# -13-[gh13.docx](https://github.com/user-attachments/files/25841017/gh13.docx)
[database.sql](https://github.com/user-attachments/files/25841029/database.sql)
USE [master]
GO
/****** Object:  Database [пр13]    Script Date: 09.03.2026 12:21:51 ******/
CREATE DATABASE [пр13]
 CONTAINMENT = NONE
 ON  PRIMARY 
( NAME = N'пр13', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.MSSQLSERVER\MSSQL\DATA\пр13.mdf' , SIZE = 8192KB , MAXSIZE = UNLIMITED, FILEGROWTH = 65536KB )
 LOG ON 
( NAME = N'пр13_log', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.MSSQLSERVER\MSSQL\DATA\пр13_log.ldf' , SIZE = 8192KB , MAXSIZE = 2048GB , FILEGROWTH = 65536KB )
 WITH CATALOG_COLLATION = DATABASE_DEFAULT, LEDGER = OFF
GO
ALTER DATABASE [пр13] SET COMPATIBILITY_LEVEL = 160
GO
IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled'))
begin
EXEC [пр13].[dbo].[sp_fulltext_database] @action = 'enable'
end
GO
ALTER DATABASE [пр13] SET ANSI_NULL_DEFAULT OFF 
GO
ALTER DATABASE [пр13] SET ANSI_NULLS OFF 
GO
ALTER DATABASE [пр13] SET ANSI_PADDING OFF 
GO
ALTER DATABASE [пр13] SET ANSI_WARNINGS OFF 
GO
ALTER DATABASE [пр13] SET ARITHABORT OFF 
GO
ALTER DATABASE [пр13] SET AUTO_CLOSE OFF 
GO
ALTER DATABASE [пр13] SET AUTO_SHRINK OFF 
GO
ALTER DATABASE [пр13] SET AUTO_UPDATE_STATISTICS ON 
GO
ALTER DATABASE [пр13] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO
ALTER DATABASE [пр13] SET CURSOR_DEFAULT  GLOBAL 
GO
ALTER DATABASE [пр13] SET CONCAT_NULL_YIELDS_NULL OFF 
GO
ALTER DATABASE [пр13] SET NUMERIC_ROUNDABORT OFF 
GO
ALTER DATABASE [пр13] SET QUOTED_IDENTIFIER OFF 
GO
ALTER DATABASE [пр13] SET RECURSIVE_TRIGGERS OFF 
GO
ALTER DATABASE [пр13] SET  DISABLE_BROKER 
GO
ALTER DATABASE [пр13] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO
ALTER DATABASE [пр13] SET DATE_CORRELATION_OPTIMIZATION OFF 
GO
ALTER DATABASE [пр13] SET TRUSTWORTHY OFF 
GO
ALTER DATABASE [пр13] SET ALLOW_SNAPSHOT_ISOLATION OFF 
GO
ALTER DATABASE [пр13] SET PARAMETERIZATION SIMPLE 
GO
ALTER DATABASE [пр13] SET READ_COMMITTED_SNAPSHOT OFF 
GO
ALTER DATABASE [пр13] SET HONOR_BROKER_PRIORITY OFF 
GO
ALTER DATABASE [пр13] SET RECOVERY SIMPLE 
GO
ALTER DATABASE [пр13] SET  MULTI_USER 
GO
ALTER DATABASE [пр13] SET PAGE_VERIFY CHECKSUM  
GO
ALTER DATABASE [пр13] SET DB_CHAINING OFF 
GO
ALTER DATABASE [пр13] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF ) 
GO
ALTER DATABASE [пр13] SET TARGET_RECOVERY_TIME = 60 SECONDS 
GO
ALTER DATABASE [пр13] SET DELAYED_DURABILITY = DISABLED 
GO
ALTER DATABASE [пр13] SET ACCELERATED_DATABASE_RECOVERY = OFF  
GO
ALTER DATABASE [пр13] SET QUERY_STORE = ON
GO
ALTER DATABASE [пр13] SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 30), DATA_FLUSH_INTERVAL_SECONDS = 900, INTERVAL_LENGTH_MINUTES = 60, MAX_STORAGE_SIZE_MB = 1000, QUERY_CAPTURE_MODE = AUTO, SIZE_BASED_CLEANUP_MODE = AUTO, MAX_PLANS_PER_QUERY = 200, WAIT_STATS_CAPTURE_MODE = ON)
GO
USE [пр13]
GO
/****** Object:  Table [dbo].[AdmissionHistory]    Script Date: 09.03.2026 12:21:51 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[AdmissionHistory](
	[AdmissionHistoryID] [int] IDENTITY(1,1) NOT NULL,
	[AdmissionType] [nvarchar](50) NULL,
	[AdmissionDate] [date] NOT NULL,
	[DonorName] [nvarchar](150) NULL,
	[PurchaseAmount] [float] NULL,
	[DocumentNumber] [nvarchar](50) NULL,
	[Notes] [nvarchar](300) NULL,
PRIMARY KEY CLUSTERED 
(
	[AdmissionHistoryID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[AuthorsCreators]    Script Date: 09.03.2026 12:21:51 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[AuthorsCreators](
	[AuthorsCreatorsID] [int] IDENTITY(1,1) NOT NULL,
	[FullName] [nvarchar](150) NOT NULL,
	[Country] [nvarchar](100) NULL,
	[BirthYear] [int] NULL,
	[DeathYear] [int] NULL,
	[Biography] [nvarchar](500) NULL,
PRIMARY KEY CLUSTERED 
(
	[AuthorsCreatorsID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Exhibitss]    Script Date: 09.03.2026 12:21:51 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Exhibitss](
	[ExhibitsID] [int] IDENTITY(1,1) NOT NULL,
	[InventoryNumber] [nvarchar](50) NOT NULL,
	[Title] [nvarchar](200) NOT NULL,
	[Description] [nvarchar](max) NULL,
	[AuthorsCreatorsID] [int] NULL,
	[CreationYear] [int] NULL,
	[Material] [nvarchar](100) NULL,
	[Dimensions] [nvarchar](100) NULL,
	[HallsStoragesID] [int] NULL,
	[ExpositionsID] [int] NULL,
	[AdmissionHistoryID] [int] NULL,
	[Condition] [nvarchar](50) NULL,
	[EstimatedValue] [int] NULL,
	[DateAdded] [date] NULL,
PRIMARY KEY CLUSTERED 
(
	[ExhibitsID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Expositions]    Script Date: 09.03.2026 12:21:51 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Expositions](
	[ExpositionsID] [int] IDENTITY(1,1) NOT NULL,
	[Title] [nvarchar](200) NOT NULL,
	[Description] [nvarchar](500) NULL,
	[StartDate] [date] NULL,
	[EndDate] [date] NULL,
	[CuratorName] [nvarchar](150) NULL,
PRIMARY KEY CLUSTERED 
(
	[ExpositionsID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[HallsStorages]    Script Date: 09.03.2026 12:21:51 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[HallsStorages](
	[HallsStoragesID] [int] IDENTITY(1,1) NOT NULL,
	[Name] [nvarchar](100) NOT NULL,
	[Type] [nvarchar](50) NULL,
	[Floor] [int] NULL,
	[Area] [decimal](10, 2) NULL,
	[TemperatureCondition] [nvarchar](50) NULL,
	[HumidityCondition] [nvarchar](50) NULL,
PRIMARY KEY CLUSTERED 
(
	[HallsStoragesID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[RestorationLogs]    Script Date: 09.03.2026 12:21:51 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[RestorationLogs](
	[RestorationID] [int] IDENTITY(1,1) NOT NULL,
	[ExhibitID] [int] NOT NULL,
	[RestorationDate] [date] NOT NULL,
	[Description] [nvarchar](500) NULL,
	[Cost] [decimal](18, 2) NULL,
	[MasterName] [nvarchar](150) NULL,
	[CompletionDate] [date] NULL,
	[Status] [nvarchar](50) NULL,
PRIMARY KEY CLUSTERED 
(
	[RestorationID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Roles]    Script Date: 09.03.2026 12:21:51 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Roles](
	[RoleID] [int] IDENTITY(1,1) NOT NULL,
	[RoleName] [nvarchar](50) NOT NULL,
	[Description] [nvarchar](200) NULL,
	[CreatedDate] [datetime] NULL,
PRIMARY KEY CLUSTERED 
(
	[RoleID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 09.03.2026 12:21:51 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[UserID] [int] IDENTITY(1,1) NOT NULL,
	[Login] [nvarchar](100) NOT NULL,
	[PasswordHash] [nvarchar](256) NOT NULL,
	[FullName] [nvarchar](150) NOT NULL,
	[Email] [nvarchar](100) NULL,
	[RoleID] [int] NOT NULL,
	[IsActive] [bit] NULL,
	[CreatedDate] [datetime] NULL,
	[LastLogin] [datetime] NULL,
PRIMARY KEY CLUSTERED 
(
	[UserID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
SET IDENTITY_INSERT [dbo].[AdmissionHistory] ON 

INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (1, N'Purchase', CAST(N'2015-03-12' AS Date), N'Частный коллекционер Иванов', 125000, N'DOC-2015-0001', N'Покупка картины на аукционе')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (2, N'Donation', CAST(N'2018-07-23' AS Date), N'Государственный музей', 0, N'DOC-2018-0002', N'Безвозмездная передача')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (3, N'Archaeological', CAST(N'2012-11-05' AS Date), N'Археологическая экспедиция', 0, N'DOC-2012-0003', N'Находка при раскопках')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (4, N'Transfer', CAST(N'2020-02-14' AS Date), N'Министерство культуры', 0, N'DOC-2020-0004', N'Передача из федерального фонда')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (5, N'Purchase', CAST(N'2016-09-30' AS Date), N'Аукционный дом Sothebys', 350000, N'DOC-2016-0005', N'Приобретение скульптуры')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (6, N'Confiscation', CAST(N'2013-04-18' AS Date), N'Частное лицо', 0, N'DOC-2013-0006', N'Конфискация незаконно вывезенного')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (7, N'Donation', CAST(N'2019-12-01' AS Date), N'Художественная галерея', 0, N'DOC-2019-0007', N'Дар от частной галереи')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (8, N'Purchase', CAST(N'2014-06-22' AS Date), N'Антикварный магазин', 89000, N'DOC-2014-0008', N'Покупка графики')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (9, N'Archaeological', CAST(N'2017-08-15' AS Date), N'Археологическая экспедиция', 0, N'DOC-2017-0009', N'Артефакт из кургана')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (10, N'Transfer', CAST(N'2021-01-28' AS Date), N'Государственный музей', 0, N'DOC-2021-0010', N'Межмузейный обмен')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (11, N'Purchase', CAST(N'2011-10-10' AS Date), N'Частный коллекционер Петров', 450000, N'DOC-2011-0011', N'Приобретение иконы')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (12, N'Donation', CAST(N'2022-05-03' AS Date), N'Частное лицо', 0, N'DOC-2022-0012', N'Пожертвование от мецената')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (13, N'Purchase', CAST(N'2015-07-19' AS Date), N'Аукционный дом Christie''s', 275000, N'DOC-2015-0013', N'Покупка пейзажа')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (14, N'Confiscation', CAST(N'2018-03-25' AS Date), N'Частное лицо', 0, N'DOC-2018-0014', N'Изъятие таможенными органами')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (15, N'Transfer', CAST(N'2013-12-08' AS Date), N'Министерство культуры', 0, N'DOC-2013-0015', N'Передача на хранение')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (16, N'Donation', CAST(N'2020-09-14' AS Date), N'Художественная галерея', 0, N'DOC-2020-0016', N'Передача из частной коллекции')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (17, N'Purchase', CAST(N'2016-02-29' AS Date), N'Антикварный салон', 165000, N'DOC-2016-0017', N'Приобретение фарфора')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (18, N'Archaeological', CAST(N'2019-06-11' AS Date), N'Институт археологии', 0, N'DOC-2019-0018', N'Находка при охранных раскопках')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (19, N'Purchase', CAST(N'2014-11-23' AS Date), N'Частный коллекционер Сидоров', 520000, N'DOC-2014-0019', N'Покупка портрета')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (20, N'Transfer', CAST(N'2021-04-07' AS Date), N'Государственный музей', 0, N'DOC-2021-0020', N'Передача из запасников')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (21, N'Donation', CAST(N'2012-08-16' AS Date), N'Частное лицо', 0, N'DOC-2012-0021', N'Дар потомков художника')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (22, N'Purchase', CAST(N'2017-01-31' AS Date), N'Аукционный дом', 395000, N'DOC-2017-0022', N'Приобретение миниатюры')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (23, N'Confiscation', CAST(N'2022-10-20' AS Date), N'Частное лицо', 0, N'DOC-2022-0023', N'Конфискация по решению суда')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (24, N'Donation', CAST(N'2015-05-12' AS Date), N'Художественная галерея', 0, N'DOC-2015-0024', N'Безвозмездная передача')
INSERT [dbo].[AdmissionHistory] ([AdmissionHistoryID], [AdmissionType], [AdmissionDate], [DonorName], [PurchaseAmount], [DocumentNumber], [Notes]) VALUES (25, N'Purchase', CAST(N'2018-12-05' AS Date), N'Антикварный магазин', 210000, N'DOC-2018-0025', N'Покупка гравюры')
SET IDENTITY_INSERT [dbo].[AdmissionHistory] OFF
GO
SET IDENTITY_INSERT [dbo].[AuthorsCreators] ON 

INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (1, N'Леонардо да Винчи', N'Италия', 1452, 1519, N'Великий итальянский художник эпохи Возрождения')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (2, N'Микеланджело Буонарроти', N'Италия', 1475, 1564, N'Итальянский скульптор, живописец, архитектор')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (3, N'Рафаэль Санти', N'Италия', 1483, 1520, N'Итальянский живописец эпохи Высокого Возрождения')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (4, N'Винсент Ван Гог', N'Нидерланды', 1853, 1890, N'Нидерландский художник-постимпрессионист')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (5, N'Пабло Пикассо', N'Испания', 1881, 1973, N'Испанский и французский художник, скульптор')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (6, N'Клод Моне', N'Франция', 1840, 1926, N'Французский живописец, основатель импрессионизма')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (7, N'Сальвадор Дали', N'Испания', 1904, 1989, N'Испанский живописец, график, скульптор')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (8, N'Рембрандт ван Рейн', N'Нидерланды', 1606, 1669, N'Великий голландский живописец')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (9, N'Иван Айвазовский', N'Россия', 1817, 1900, N'Русский художник-маринист')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (10, N'Илья Репин', N'Россия', 1844, 1930, N'Русский живописец, передвижник')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (11, N'Василий Кандинский', N'Россия', 1866, 1944, N'Русский и немецкий художник, абстракционист')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (12, N'Казимир Малевич', N'Россия', 1879, 1935, N'Русский художник-авангардист, супрематист')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (13, N'Марк Шагал', N'Россия', 1887, 1985, N'Русский и французский художник-авангардист')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (14, N'Анри Матисс', N'Франция', 1869, 1954, N'Французский живописец, лидер фовизма')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (15, N'Поль Сезанн', N'Франция', 1839, 1906, N'Французский живописец, постимпрессионист')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (16, N'Эдгар Дега', N'Франция', 1834, 1917, N'Французский живописец, импрессионист')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (17, N'Густав Климт', N'Австрия', 1862, 1918, N'Австрийский живописец, символист')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (18, N'Эдвард Мунк', N'Норвегия', 1863, 1944, N'Норвежский живописец, экспрессионист')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (19, N'Диего Веласкес', N'Испания', 1599, 1660, N'Испанский живописец, придворный художник')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (20, N'Ян Вермеер', N'Нидерланды', 1632, 1675, N'Нидерландский живописец, мастер света')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (21, N'Сандро Боттичелли', N'Италия', 1445, 1510, N'Итальянский живописец раннего Возрождения')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (22, N'Тициан', N'Италия', 1488, 1576, N'Итальянский живописец, венецианская школа')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (23, N'Караваджо', N'Италия', 1571, 1610, N'Итальянский живописец, мастер барокко')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (24, N'Франсиско Гойя', N'Испания', 1746, 1828, N'Испанский живописец и график')
INSERT [dbo].[AuthorsCreators] ([AuthorsCreatorsID], [FullName], [Country], [BirthYear], [DeathYear], [Biography]) VALUES (25, N'Эжен Делакруа', N'Франция', 1798, 1863, N'Французский живописец, романтик')
SET IDENTITY_INSERT [dbo].[AuthorsCreators] OFF
GO
SET IDENTITY_INSERT [dbo].[Exhibitss] ON 

INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (1, N'INV-2024-00001', N'Портрет дамы', N'Уникальный экспонат музейной коллекции', 8, 1678, N'Холст, масло', N'85 x 120 см', 6, 5, 14, N'Good', 125000, CAST(N'2021-03-15' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (2, N'INV-2024-00002', N'Пейзаж с рекой', N'Историческая и художественная ценность', 15, 1823, N'Дерево, темпера', N'120 x 95 см', 3, 8, 7, N'Excellent', 285000, CAST(N'2022-07-22' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (3, N'INV-2024-00003', N'Натюрморт с фруктами', N'Произведение искусства XIX века', 22, 1756, N'Бумага, акварель', N'45 x 60 см', 7, 12, 19, N'Satisfactory', 95000, CAST(N'2020-11-08' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (4, N'INV-2024-00004', N'Битва при Ватерлоо', N'Историческая батальная сцена', 3, 1889, N'Холст, пастель', N'200 x 150 см', 1, 3, 2, N'Poor', 450000, CAST(N'2023-02-14' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (5, N'INV-2024-00005', N'Мадонна с младенцем', N'Религиозная композиция эпохи Возрождения', 2, 1503, N'Дерево, темпера', N'180 x 120 см', 8, 1, 11, N'Restoration', 850000, CAST(N'2021-09-30' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (6, N'INV-2024-00006', N'Автопортрет художника', N'Автопортрет в зрелом возрасте', 18, 1912, N'Холст, масло', N'75 x 65 см', 5, 20, 4, N'Good', 320000, CAST(N'2022-04-18' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (7, N'INV-2024-00007', N'Вид Венеции', N'Городской пейзаж Италии', 6, 1875, N'Бумага, тушь', N'55 x 80 см', 10, 2, 16, N'Excellent', 175000, CAST(N'2020-06-25' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (8, N'INV-2024-00008', N'Сцена из античной жизни', N'Мифологический сюжет', 21, 1485, N'Дерево, резьба', N'95 x 140 см', 22, 7, 23, N'Satisfactory', 520000, CAST(N'2023-01-12' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (9, N'INV-2024-00009', N'Религиозная композиция', N'Библейский сюжет', 2, 1534, N'Холст, масло', N'250 x 180 см', 6, 6, 9, N'Good', 950000, CAST(N'2021-12-03' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (10, N'INV-2024-00010', N'Мифологическая сцена', N'Сцена из древнегреческой мифологии', 19, 1642, N'Медь, гравюра', N'35 x 45 см', 15, 10, 5, N'Excellent', 85000, CAST(N'2022-08-19' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (11, N'INV-2024-00011', N'Историческое событие', N'Важное историческое событие', 10, 1895, N'Холст, масло', N'180 x 250 см', 7, 3, 12, N'Poor', 380000, CAST(N'2020-03-27' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (12, N'INV-2024-00012', N'Портрет мужчины в доспехах', N'Парадный портрет', 23, 1605, N'Холст, масло', N'110 x 85 см', 1, 9, 18, N'Good', 425000, CAST(N'2023-05-14' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (13, N'INV-2024-00013', N'Зимний пейзаж', N'Зимний ландшафт', 9, 1867, N'Холст, масло', N'95 x 130 см', 3, 14, 1, N'Excellent', 295000, CAST(N'2021-01-20' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (14, N'INV-2024-00014', N'Весенний мотив', N'Весенний пейзаж', 4, 1888, N'Холст, масло', N'73 x 92 см', 4, 2, 6, N'Satisfactory', 680000, CAST(N'2022-10-08' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (15, N'INV-2024-00015', N'Летний день', N'Летний пейзаж', 14, 1905, N'Бумага, акварель', N'48 x 65 см', 11, 15, 21, N'Good', 145000, CAST(N'2020-07-16' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (16, N'INV-2024-00016', N'Осенний пейзаж', N'Осенний ландшафт', 15, 1890, N'Холст, масло', N'65 x 81 см', 3, 14, 15, N'Restoration', 520000, CAST(N'2023-03-29' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (17, N'INV-2024-00017', N'Морской вид', N'Морской пейзаж', 9, 1856, N'Холст, масло', N'125 x 185 см', 1, 1, 8, N'Excellent', 385000, CAST(N'2021-06-11' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (18, N'INV-2024-00018', N'Горный ландшафт', N'Горный пейзаж', 17, 1908, N'Холст, масло', N'88 x 112 см', 5, 19, 3, N'Good', 235000, CAST(N'2022-12-05' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (19, N'INV-2024-00019', N'Интерьер дворца', N'Дворцовый интерьер', 20, 1665, N'Холст, масло', N'76 x 64 см', 9, 11, 20, N'Satisfactory', 475000, CAST(N'2020-09-23' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (20, N'INV-2024-00020', N'Архитектурный этюд', N'Архитектурный рисунок', 7, 1931, N'Бумага, тушь', N'42 x 58 см', 12, 22, 10, N'Poor', 165000, CAST(N'2023-04-17' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (21, N'INV-2024-00021', N'Цветочная композиция', N'Натюрморт с цветами', 13, 1925, N'Холст, масло', N'92 x 73 см', 4, 13, 17, N'Good', 195000, CAST(N'2021-11-28' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (22, N'INV-2024-00022', N'Портрет ребенка', N'Детский портрет', 8, 1642, N'Холст, масло', N'68 x 55 см', 7, 13, 25, N'Excellent', 340000, CAST(N'2022-02-14' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (23, N'INV-2024-00023', N'Семейный портрет', N'Групповой семейный портрет', 19, 1656, N'Холст, масло', N'195 x 265 см', 1, 9, 14, N'Satisfactory', 780000, CAST(N'2020-05-09' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (24, N'INV-2024-00024', N'Групповой портрет', N'Портрет группы людей', 10, 1887, N'Холст, масло', N'152 x 225 см', 7, 3, 22, N'Good', 425000, CAST(N'2023-08-31' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (25, N'INV-2024-00025', N'Аллегория времени', N'Символическая композиция', 24, 1799, N'Холст, масло', N'130 x 97 см', 5, 18, 11, N'Restoration', 315000, CAST(N'2021-04-22' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (26, N'INV-2024-00026', N'Символическая композиция', N'Абстрактная символика', 11, 1913, N'Холст, масло', N'140 x 140 см', 5, 23, 6, N'Excellent', 890000, CAST(N'2022-01-15' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (27, N'INV-2024-00027', N'Портрет дамы', N'Портрет знатной дамы', 5, 1907, N'Холст, масло', N'92 x 73 см', 10, 21, 19, N'Good', 1250000, CAST(N'2020-10-03' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (28, N'INV-2024-00028', N'Пейзаж с рекой', N'Речной пейзаж', 6, 1872, N'Холст, масло', N'89 x 116 см', 4, 2, 13, N'Satisfactory', 485000, CAST(N'2023-06-19' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (29, N'INV-2024-00029', N'Натюрморт с фруктами', N'Фруктовый натюрморт', 15, 1885, N'Холст, масло', N'65 x 81 см', 3, 15, 24, N'Poor', 395000, CAST(N'2021-08-07' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (30, N'INV-2024-00030', N'Битва при Ватерлоо', N'Военная батальная сцена', 25, 1831, N'Холст, масло', N'285 x 380 см', 1, 17, 4, N'Good', 1150000, CAST(N'2022-03-26' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (31, N'INV-2024-00031', N'Мадонна с младенцем', N'Религиозная живопись', 3, 1512, N'Дерево, темпера', N'105 x 75 см', 8, 1, 16, N'Excellent', 920000, CAST(N'2020-12-14' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (32, N'INV-2024-00032', N'Автопортрет художника', N'Автопортрет в мастерской', 4, 1889, N'Холст, масло', N'65 x 54 см', 5, 2, 8, N'Restoration', 750000, CAST(N'2023-02-28' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (33, N'INV-2024-00033', N'Вид Венеции', N'Венецианский пейзаж', 22, 1545, N'Дерево, темпера', N'115 x 145 см', 1, 9, 1, N'Satisfactory', 685000, CAST(N'2021-05-16' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (34, N'INV-2024-00034', N'Сцена из античной жизни', N'Античный сюжет', 2, 1508, N'Холст, масло', N'170 x 210 см', 6, 6, 20, N'Good', 825000, CAST(N'2022-09-11' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (35, N'INV-2024-00035', N'Религиозная композиция', N'Христианский сюжет', 21, 1482, N'Дерево, темпера', N'205 x 172 см', 8, 7, 12, N'Excellent', 1050000, CAST(N'2020-04-05' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (36, N'INV-2024-00036', N'Мифологическая сцена', N'Мифологический сюжет', 17, 1901, N'Холст, масло', N'138 x 138 см', 5, 19, 25, N'Poor', 445000, CAST(N'2023-07-23' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (37, N'INV-2024-00037', N'Историческое событие', N'Историческая сцена', 25, 1830, N'Холст, масло', N'260 x 325 см', 1, 17, 7, N'Good', 975000, CAST(N'2021-10-18' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (38, N'INV-2024-00038', N'Портрет мужчины в доспехах', N'Рыцарский портрет', 19, 1635, N'Холст, масло', N'98 x 78 см', 7, 10, 15, N'Satisfactory', 385000, CAST(N'2022-06-29' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (39, N'INV-2024-00039', N'Зимний пейзаж', N'Зимняя природа', 8, 1665, N'Дерево, масло', N'72 x 95 см', 3, 10, 2, N'Excellent', 425000, CAST(N'2020-01-24' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (40, N'INV-2024-00040', N'Весенний мотив', N'Весенняя природа', 6, 1876, N'Холст, масло', N'78 x 102 см', 4, 2, 18, N'Good', 565000, CAST(N'2023-09-12' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (41, N'INV-2024-00041', N'Летний день', N'Летний пейзаж', 14, 1910, N'Холст, масло', N'85 x 115 см', 11, 16, 9, N'Restoration', 295000, CAST(N'2021-02-07' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (42, N'INV-2024-00042', N'Осенний пейзаж', N'Осенняя природа', 15, 1888, N'Холст, масло', N'73 x 92 см', 3, 14, 21, N'Satisfactory', 485000, CAST(N'2022-11-19' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (43, N'INV-2024-00043', N'Морской вид', N'Морской пейзаж', 9, 1873, N'Холст, масло', N'135 x 195 см', 1, 1, 5, N'Good', 395000, CAST(N'2020-08-15' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (44, N'INV-2024-00044', N'Горный ландшафт', N'Горы', 18, 1893, N'Холст, масло', N'102 x 125 см', 5, 20, 14, N'Excellent', 335000, CAST(N'2023-01-30' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (45, N'INV-2024-00045', N'Интерьер дворца', N'Дворцовый зал', 20, 1658, N'Холст, масло', N'82 x 68 см', 9, 11, 23, N'Poor', 525000, CAST(N'2021-07-25' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (46, N'INV-2024-00046', N'Архитектурный этюд', N'Архитектура', 7, 1928, N'Бумага, акварель', N'38 x 52 см', 12, 22, 11, N'Good', 185000, CAST(N'2022-04-13' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (47, N'INV-2024-00047', N'Цветочная композиция', N'Цветы', 13, 1918, N'Холст, масло', N'88 x 116 см', 4, 13, 6, N'Satisfactory', 225000, CAST(N'2020-11-28' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (48, N'INV-2024-00048', N'Портрет ребенка', N'Детский портрет', 8, 1650, N'Холст, масло', N'62 x 50 см', 7, 13, 17, N'Excellent', 365000, CAST(N'2023-03-16' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (49, N'INV-2024-00049', N'Семейный портрет', N'Семья', 19, 1642, N'Холст, масло', N'205 x 275 см', 1, 9, 24, N'Good', 825000, CAST(N'2021-12-21' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (50, N'INV-2024-00050', N'Групповой портрет', N'Группа людей', 10, 1891, N'Холст, масло', N'165 x 235 см', 7, 3, 3, N'Restoration', 465000, CAST(N'2022-08-08' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (51, N'INV-2024-00051', N'Аллегория времени', N'Время', 24, 1805, N'Холст, масло', N'145 x 110 см', 5, 18, 12, N'Good', 355000, CAST(N'2020-02-18' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (52, N'INV-2024-00052', N'Символическая композиция', N'Символизм', 11, 1920, N'Холст, масло', N'155 x 155 см', 5, 23, 7, N'Excellent', 920000, CAST(N'2023-05-25' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (53, N'INV-2024-00053', N'Портрет дамы', N'Женский портрет', 5, 1912, N'Холст, масло', N'88 x 68 см', 10, 21, 20, N'Satisfactory', 1150000, CAST(N'2021-09-14' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (54, N'INV-2024-00054', N'Пейзаж с рекой', N'Река', 6, 1878, N'Холст, масло', N'95 x 125 см', 4, 2, 14, N'Poor', 525000, CAST(N'2022-01-30' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (55, N'INV-2024-00055', N'Натюрморт с фруктами', N'Фрукты', 15, 1892, N'Холст, масло', N'72 x 88 см', 3, 15, 25, N'Good', 415000, CAST(N'2020-06-22' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (56, N'INV-2024-00056', N'Битва при Ватерлоо', N'Сражение', 25, 1835, N'Холст, масло', N'295 x 390 см', 1, 17, 5, N'Restoration', 1250000, CAST(N'2023-10-08' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (57, N'INV-2024-00057', N'Мадонна с младенцем', N'Мадонна', 3, 1518, N'Дерево, темпера', N'112 x 82 см', 8, 1, 17, N'Excellent', 980000, CAST(N'2021-03-19' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (58, N'INV-2024-00058', N'Автопортрет художника', N'Автопортрет', 4, 1887, N'Холст, масло', N'68 x 58 см', 5, 2, 9, N'Satisfactory', 795000, CAST(N'2022-07-05' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (59, N'INV-2024-00059', N'Вид Венеции', N'Венеция', 22, 1552, N'Дерево, темпера', N'122 x 152 см', 1, 9, 2, N'Good', 725000, CAST(N'2020-11-17' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (60, N'INV-2024-00060', N'Сцена из античной жизни', N'Античность', 2, 1515, N'Холст, масло', N'178 x 218 см', 6, 6, 21, N'Excellent', 885000, CAST(N'2023-04-03' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (61, N'INV-2024-00061', N'Религиозная композиция', N'Религия', 21, 1488, N'Дерево, темпера', N'212 x 178 см', 8, 7, 13, N'Poor', 1120000, CAST(N'2021-08-26' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (62, N'INV-2024-00062', N'Мифологическая сцена', N'Мифология', 17, 1908, N'Холст, масло', N'145 x 145 см', 5, 19, 24, N'Good', 485000, CAST(N'2022-12-12' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (63, N'INV-2024-00063', N'Историческое событие', N'История', 25, 1838, N'Холст, масло', N'268 x 332 см', 1, 17, 8, N'Satisfactory', 1025000, CAST(N'2020-05-29' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (64, N'INV-2024-00064', N'Портрет мужчины в доспехах', N'Доспехи', 19, 1642, N'Холст, масло', N'105 x 85 см', 7, 10, 16, N'Restoration', 425000, CAST(N'2023-01-21' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (65, N'INV-2024-00065', N'Зимний пейзаж', N'Зима', 8, 1672, N'Дерево, масло', N'78 x 102 см', 3, 10, 3, N'Excellent', 465000, CAST(N'2021-06-08' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (66, N'INV-2024-00066', N'Весенний мотив', N'Весна', 6, 1882, N'Холст, масло', N'85 x 108 см', 4, 2, 19, N'Good', 595000, CAST(N'2022-10-24' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (67, N'INV-2024-00067', N'Летний день', N'Лето', 14, 1915, N'Холст, масло', N'92 x 122 см', 11, 16, 10, N'Satisfactory', 325000, CAST(N'2020-03-15' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (68, N'INV-2024-00068', N'Осенний пейзаж', N'Осень', 15, 1895, N'Холст, масло', N'80 x 98 см', 3, 14, 22, N'Poor', 515000, CAST(N'2023-07-09' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (69, N'INV-2024-00069', N'Морской вид', N'Море', 9, 1878, N'Холст, масло', N'142 x 202 см', 1, 1, 6, N'Good', 425000, CAST(N'2021-11-03' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (70, N'INV-2024-00070', N'Горный ландшафт', N'Горы', 18, 1898, N'Холст, масло', N'108 x 132 см', 5, 20, 15, N'Excellent', 365000, CAST(N'2022-04-27' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (71, N'INV-2024-00071', N'Интерьер дворца', N'Интерьер', 20, 1662, N'Холст, масло', N'88 x 72 см', 9, 11, 24, N'Restoration', 565000, CAST(N'2020-09-11' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (72, N'INV-2024-00072', N'Архитектурный этюд', N'Архитектура', 7, 1935, N'Бумага, акварель', N'45 x 58 см', 12, 22, 12, N'Good', 195000, CAST(N'2023-02-16' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (73, N'INV-2024-00073', N'Цветочная композиция', N'Цветы', 13, 1922, N'Холст, масло', N'95 x 122 см', 4, 13, 7, N'Satisfactory', 245000, CAST(N'2021-05-30' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (74, N'INV-2024-00074', N'Портрет ребенка', N'Ребенок', 8, 1655, N'Холст, масло', N'68 x 55 см', 7, 13, 18, N'Excellent', 385000, CAST(N'2022-08-22' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (75, N'INV-2024-00075', N'Семейный портрет', N'Семья', 19, 1648, N'Холст, масло', N'212 x 282 см', 1, 9, 25, N'Good', 865000, CAST(N'2020-12-05' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (76, N'INV-2024-00076', N'Групповой портрет', N'Группа', 10, 1895, N'Холст, масло', N'172 x 242 см', 7, 3, 4, N'Poor', 485000, CAST(N'2023-06-18' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (77, N'INV-2024-00077', N'Аллегория времени', N'Аллегория', 24, 1812, N'Холст, масло', N'138 x 105 см', 5, 18, 13, N'Restoration', 375000, CAST(N'2021-10-09' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (78, N'INV-2024-00078', N'Символическая композиция', N'Символ', 11, 1925, N'Холст, масло', N'148 x 148 см', 5, 23, 8, N'Good', 950000, CAST(N'2022-02-23' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (79, N'INV-2024-00079', N'Портрет дамы', N'Дама', 5, 1918, N'Холст, масло', N'95 x 75 см', 10, 21, 21, N'Satisfactory', 1180000, CAST(N'2020-07-14' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (80, N'INV-2024-00080', N'Пейзаж с рекой', N'Пейзаж', 6, 1885, N'Холст, масло', N'102 x 132 см', 4, 2, 15, N'Excellent', 545000, CAST(N'2023-11-27' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (81, N'INV-2024-00081', N'Натюрморт с фруктами', N'Натюрморт', 15, 1898, N'Холст, масло', N'78 x 95 см', 3, 15, 1, N'Good', 435000, CAST(N'2021-04-11' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (82, N'INV-2024-00082', N'Битва при Ватерлоо', N'Битва', 25, 1842, N'Холст, масло', N'302 x 398 см', 1, 17, 6, N'Poor', 1320000, CAST(N'2022-09-05' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (83, N'INV-2024-00083', N'Мадонна с младенцем', N'Мадонна', 3, 1525, N'Дерево, темпера', N'118 x 88 см', 8, 1, 18, N'Restoration', 1020000, CAST(N'2020-01-28' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (84, N'INV-2024-00084', N'Автопортрет художника', N'Портрет', 4, 1890, N'Холст, масло', N'72 x 62 см', 5, 2, 10, N'Satisfactory', 825000, CAST(N'2023-05-13' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (85, N'INV-2024-00085', N'Вид Венеции', N'Венеция', 22, 1558, N'Дерево, темпера', N'128 x 158 см', 1, 9, 3, N'Good', 765000, CAST(N'2021-12-20' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (86, N'INV-2024-00086', N'Сцена из античной жизни', N'Сцена', 2, 1522, N'Холст, масло', N'185 x 225 см', 6, 6, 22, N'Excellent', 925000, CAST(N'2022-06-16' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (87, N'INV-2024-00087', N'Религиозная композиция', N'Композиция', 21, 1495, N'Дерево, темпера', N'218 x 185 см', 8, 7, 14, N'Poor', 1180000, CAST(N'2020-10-31' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (88, N'INV-2024-00088', N'Мифологическая сцена', N'Сцена', 17, 1915, N'Холст, масло', N'152 x 152 см', 5, 19, 25, N'Good', 525000, CAST(N'2023-03-08' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (89, N'INV-2024-00089', N'Историческое событие', N'Событие', 25, 1845, N'Холст, масло', N'275 x 340 см', 1, 17, 9, N'Restoration', 1085000, CAST(N'2021-07-22' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (90, N'INV-2024-00090', N'Портрет мужчины в доспехах', N'Мужчина', 19, 1648, N'Холст, масло', N'112 x 92 см', 7, 10, 17, N'Satisfactory', 465000, CAST(N'2022-11-14' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (91, N'INV-2024-00091', N'Зимний пейзаж', N'Пейзаж', 8, 1678, N'Дерево, масло', N'85 x 108 см', 3, 10, 4, N'Excellent', 495000, CAST(N'2020-04-06' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (92, N'INV-2024-00092', N'Весенний мотив', N'Мотив', 6, 1888, N'Холст, масло', N'92 x 115 см', 4, 2, 20, N'Good', 625000, CAST(N'2023-08-19' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (93, N'INV-2024-00093', N'Летний день', N'День', 14, 1920, N'Холст, масло', N'98 x 128 см', 11, 16, 11, N'Poor', 355000, CAST(N'2021-01-25' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (94, N'INV-2024-00094', N'Осенний пейзаж', N'Пейзаж', 15, 1902, N'Холст, масло', N'88 x 105 см', 3, 14, 23, N'Restoration', 545000, CAST(N'2022-05-10' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (95, N'INV-2024-00095', N'Морской вид', N'Вид', 9, 1885, N'Холст, масло', N'148 x 208 см', 1, 1, 7, N'Satisfactory', 455000, CAST(N'2020-08-23' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (96, N'INV-2024-00096', N'Горный ландшафт', N'Ландшафт', 18, 1905, N'Холст, масло', N'115 x 138 см', 5, 20, 16, N'Good', 395000, CAST(N'2023-12-01' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (97, N'INV-2024-00097', N'Интерьер дворца', N'Дворец', 20, 1668, N'Холст, масло', N'95 x 78 см', 9, 11, 25, N'Excellent', 595000, CAST(N'2021-09-17' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (98, N'INV-2024-00098', N'Архитектурный этюд', N'Этюд', 7, 1940, N'Бумага, акварель', N'52 x 65 см', 12, 22, 13, N'Good', 215000, CAST(N'2022-03-04' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (99, N'INV-2024-00099', N'Цветочная композиция', N'Композиция', 13, 1928, N'Холст, масло', N'102 x 128 см', 4, 13, 8, N'Poor', 265000, CAST(N'2020-06-19' AS Date))
GO
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (100, N'INV-2024-00100', N'Портрет ребенка', N'Ребенок', 8, 1660, N'Холст, масло', N'75 x 62 см', 7, 13, 19, N'Restoration', 405000, CAST(N'2023-10-26' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (101, N'INV-2024-00101', N'Семейный портрет', N'Портрет', 19, 1655, N'Холст, масло', N'218 x 288 см', 1, 9, 1, N'Satisfactory', 895000, CAST(N'2021-02-12' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (102, N'INV-2024-00102', N'Групповой портрет', N'Портрет', 10, 1898, N'Холст, масло', N'178 x 248 см', 7, 3, 5, N'Good', 505000, CAST(N'2022-07-28' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (103, N'INV-2024-00103', N'Аллегория времени', N'Время', 24, 1818, N'Холст, масло', N'145 x 112 см', 5, 18, 14, N'Excellent', 395000, CAST(N'2020-11-09' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (104, N'INV-2024-00104', N'Символическая композиция', N'Композиция', 11, 1930, N'Холст, масло', N'155 x 155 см', 5, 23, 9, N'Poor', 980000, CAST(N'2023-04-21' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (105, N'INV-2024-00105', N'Портрет дамы', N'Дама', 5, 1925, N'Холст, масло', N'98 x 78 см', 10, 21, 22, N'Restoration', 1220000, CAST(N'2021-08-05' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (106, N'INV-2024-00106', N'Пейзаж с рекой', N'Река', 6, 1892, N'Холст, масло', N'108 x 138 см', 4, 2, 16, N'Good', 565000, CAST(N'2022-12-18' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (107, N'INV-2024-00107', N'Натюрморт с фруктами', N'Фрукты', 15, 1905, N'Холст, масло', N'85 x 102 см', 3, 15, 1, N'Satisfactory', 455000, CAST(N'2020-05-03' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (108, N'INV-2024-00108', N'Битва при Ватерлоо', N'Битва', 25, 1850, N'Холст, масло', N'310 x 405 см', 1, 17, 7, N'Excellent', 1380000, CAST(N'2023-09-14' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (109, N'INV-2024-00109', N'Мадонна с младенцем', N'Мадонна', 3, 1532, N'Дерево, темпера', N'125 x 95 см', 8, 1, 19, N'Good', 1080000, CAST(N'2021-06-27' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (110, N'INV-2024-00110', N'Автопортрет художника', N'Портрет', 4, 1895, N'Холст, масло', N'78 x 68 см', 5, 2, 11, N'Poor', 855000, CAST(N'2022-10-11' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (111, N'INV-2024-00111', N'Вид Венеции', N'Венеция', 22, 1565, N'Дерево, темпера', N'135 x 165 см', 1, 9, 4, N'Restoration', 795000, CAST(N'2020-02-24' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (112, N'INV-2024-00112', N'Сцена из античной жизни', N'Античность', 2, 1528, N'Холст, масло', N'192 x 232 см', 6, 6, 23, N'Satisfactory', 965000, CAST(N'2023-07-07' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (113, N'INV-2024-00113', N'Религиозная композиция', N'Религия', 21, 1502, N'Дерево, темпера', N'225 x 192 см', 8, 7, 15, N'Good', 1240000, CAST(N'2021-11-20' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (114, N'INV-2024-00114', N'Мифологическая сцена', N'Миф', 17, 1922, N'Холст, масло', N'158 x 158 см', 5, 19, 1, N'Excellent', 565000, CAST(N'2022-04-02' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (115, N'INV-2024-00115', N'Историческое событие', N'Событие', 25, 1852, N'Холст, масло', N'282 x 348 см', 1, 17, 10, N'Poor', 1145000, CAST(N'2020-09-15' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (116, N'INV-2024-00116', N'Портрет мужчины в доспехах', N'Портрет', 19, 1655, N'Холст, масло', N'118 x 98 см', 7, 10, 18, N'Restoration', 495000, CAST(N'2023-01-28' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (117, N'INV-2024-00117', N'Зимний пейзаж', N'Зима', 8, 1685, N'Дерево, масло', N'92 x 115 см', 3, 10, 5, N'Satisfactory', 525000, CAST(N'2021-05-11' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (118, N'INV-2024-00118', N'Весенний мотив', N'Весна', 6, 1895, N'Холст, масло', N'98 x 122 см', 4, 2, 21, N'Good', 655000, CAST(N'2022-08-24' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (119, N'INV-2024-00119', N'Летний день', N'Лето', 14, 1928, N'Холст, масло', N'105 x 135 см', 11, 16, 12, N'Excellent', 385000, CAST(N'2020-12-07' AS Date))
INSERT [dbo].[Exhibitss] ([ExhibitsID], [InventoryNumber], [Title], [Description], [AuthorsCreatorsID], [CreationYear], [Material], [Dimensions], [HallsStoragesID], [ExpositionsID], [AdmissionHistoryID], [Condition], [EstimatedValue], [DateAdded]) VALUES (120, N'INV-2024-00120', N'Осенний пейзаж', N'Осень', 15, 1910, N'Холст, масло', N'95 x 112 см', 3, 14, 24, N'Good', 575000, CAST(N'2023-06-30' AS Date))
SET IDENTITY_INSERT [dbo].[Exhibitss] OFF
GO
SET IDENTITY_INSERT [dbo].[Expositions] ON 

INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (1, N'Шедевры эпохи Возрождения', N'Выставка работ великих мастеров Италии XV-XVI веков', CAST(N'2024-01-15' AS Date), CAST(N'2024-06-15' AS Date), N'Иванова А.П.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (2, N'Импрессионизм и постимпрессионизм', N'Французская живопись конца XIX - начала XX века', CAST(N'2024-02-01' AS Date), CAST(N'2024-07-01' AS Date), N'Петрова М.С.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (3, N'Русское искусство XVIII-XX веков', N'Классики русской живописи', CAST(N'2024-01-10' AS Date), CAST(N'2024-12-31' AS Date), N'Сидорова Е.В.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (4, N'Сокровища древнего мира', N'Археологические находки и артефакты', CAST(N'2024-03-01' AS Date), CAST(N'2024-08-31' AS Date), N'Козлов Д.А.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (5, N'Современное искусство', N'Актуальные тенденции в искусстве XXI века', CAST(N'2024-04-01' AS Date), CAST(N'2024-09-30' AS Date), N'Новикова О.И.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (6, N'Скульптура от античности до наших дней', N'История скульптурного искусства', CAST(N'2024-01-01' AS Date), CAST(N'2024-12-31' AS Date), N'Волков С.П.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (7, N'Иконопись Древней Руси', N'Духовное искусство русских иконописцев', CAST(N'2024-02-15' AS Date), CAST(N'2024-11-15' AS Date), N'Лебедева Т.Н.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (8, N'Авангард начала XX века', N'Революция в искусстве', CAST(N'2024-03-15' AS Date), CAST(N'2024-10-15' AS Date), N'Кузнецов А.В.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (9, N'Испанская живопись', N'От Эль Греко до Пикассо', CAST(N'2024-04-15' AS Date), CAST(N'2024-11-30' AS Date), N'Морозова И.С.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (10, N'Голландский золотой век', N'Мастера нидерландской живописи XVII века', CAST(N'2024-05-01' AS Date), CAST(N'2024-12-15' AS Date), N'Павлов Д.М.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (11, N'Декоративно-прикладное искусство Востока', N'Шедевры искусства Азии', CAST(N'2024-01-20' AS Date), CAST(N'2024-07-20' AS Date), N'Соколова Н.А.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (12, N'Графика великих мастеров', N'Рисунки, эскизы и гравюры', CAST(N'2024-02-10' AS Date), CAST(N'2024-08-10' AS Date), N'Васильев П.Р.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (13, N'Портрет в европейском искусстве', N'От Ренессанса до модерна', CAST(N'2024-03-01' AS Date), CAST(N'2024-09-01' AS Date), N'Никитина О.В.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (14, N'Пейзажная живопись', N'Природа в искусстве', CAST(N'2024-04-01' AS Date), CAST(N'2024-10-01' AS Date), N'Семенов К.Л.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (15, N'Натюрморт', N'Жанр натюрморта в европейской живописи', CAST(N'2024-05-15' AS Date), CAST(N'2024-11-15' AS Date), N'Федорова М.Д.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (16, N'Искусство модерна', N'Стиль эпохи', CAST(N'2024-01-05' AS Date), CAST(N'2024-06-30' AS Date), N'Коновалов С.И.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (17, N'Барокко и рококо', N'Пышность барокко и изящество рококо', CAST(N'2024-02-20' AS Date), CAST(N'2024-08-20' AS Date), N'Михайлова А.Е.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (18, N'Реализм в искусстве', N'Правда жизни', CAST(N'2024-03-10' AS Date), CAST(N'2024-09-10' AS Date), N'Алексеев Д.В.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (19, N'Символизм', N'Тайны и образы', CAST(N'2024-04-20' AS Date), CAST(N'2024-10-20' AS Date), N'Борисова Е.П.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (20, N'Экспрессионизм', N'Эмоции и чувства', CAST(N'2024-05-10' AS Date), CAST(N'2024-11-10' AS Date), N'Григорьев М.С.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (21, N'Кубизм', N'Новое видение формы', CAST(N'2024-01-25' AS Date), CAST(N'2024-07-25' AS Date), N'Захарова О.Л.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (22, N'Сюрреализм', N'Мир сновидений', CAST(N'2024-02-25' AS Date), CAST(N'2024-08-25' AS Date), N'Иванов П.К.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (23, N'Абстрактное искусство', N'Беспредметная живопись', CAST(N'2024-03-20' AS Date), CAST(N'2024-09-20' AS Date), N'Кудрявцева Н.М.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (24, N'Поп-арт', N'Искусство массовой культуры', CAST(N'2024-04-10' AS Date), CAST(N'2024-10-10' AS Date), N'Лебедев С.А.')
INSERT [dbo].[Expositions] ([ExpositionsID], [Title], [Description], [StartDate], [EndDate], [CuratorName]) VALUES (25, N'Минимализм', N'Простота формы', CAST(N'2024-05-20' AS Date), CAST(N'2024-11-20' AS Date), N'Максимова И.В.')
SET IDENTITY_INSERT [dbo].[Expositions] OFF
GO
SET IDENTITY_INSERT [dbo].[HallsStorages] ON 

INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (1, N'Главный выставочный зал', N'Hall', 1, CAST(500.00 AS Decimal(10, 2)), N'+20°C', N'50%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (2, N'Зал древнего искусства', N'Hall', 1, CAST(350.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (3, N'Зал живописи XIX века', N'Hall', 2, CAST(400.00 AS Decimal(10, 2)), N'+20°C', N'50%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (4, N'Зал импрессионистов', N'Hall', 2, CAST(380.00 AS Decimal(10, 2)), N'+19°C', N'48%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (5, N'Зал современного искусства', N'Hall', 3, CAST(450.00 AS Decimal(10, 2)), N'+21°C', N'52%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (6, N'Зал скульптуры', N'Hall', 1, CAST(600.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (7, N'Зал русского искусства', N'Hall', 2, CAST(420.00 AS Decimal(10, 2)), N'+20°C', N'50%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (8, N'Зал иконописи', N'Hall', 1, CAST(300.00 AS Decimal(10, 2)), N'+16°C', N'40%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (9, N'Зал декоративно-прикладного искусства', N'Hall', 3, CAST(350.00 AS Decimal(10, 2)), N'+20°C', N'50%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (10, N'Выставочный зал №1', N'Hall', 2, CAST(280.00 AS Decimal(10, 2)), N'+20°C', N'50%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (11, N'Выставочный зал №2', N'Hall', 2, CAST(280.00 AS Decimal(10, 2)), N'+20°C', N'50%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (12, N'Зал временных выставок', N'Hall', 3, CAST(500.00 AS Decimal(10, 2)), N'+20°C', N'50%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (13, N'Основное хранилище', N'Storage', 0, CAST(1000.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (14, N'Хранилище живописи', N'Storage', 0, CAST(600.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (15, N'Хранилище графики', N'Storage', 0, CAST(400.00 AS Decimal(10, 2)), N'+16°C', N'40%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (16, N'Хранилище скульптуры', N'Storage', 0, CAST(800.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (17, N'Хранилище декоративного искусства', N'Storage', 0, CAST(500.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (18, N'Реставрационная мастерская', N'Storage', 1, CAST(350.00 AS Decimal(10, 2)), N'+22°C', N'55%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (19, N'Фондохранилище №1', N'Storage', 0, CAST(700.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (20, N'Фондохранилище №2', N'Storage', 0, CAST(700.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (21, N'Зал нумизматики', N'Hall', 2, CAST(250.00 AS Decimal(10, 2)), N'+18°C', N'40%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (22, N'Зал археологии', N'Hall', 1, CAST(320.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (23, N'Зал этнографии', N'Hall', 3, CAST(380.00 AS Decimal(10, 2)), N'+20°C', N'50%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (24, N'Лапидарий', N'Hall', 0, CAST(450.00 AS Decimal(10, 2)), N'+18°C', N'45%')
INSERT [dbo].[HallsStorages] ([HallsStoragesID], [Name], [Type], [Floor], [Area], [TemperatureCondition], [HumidityCondition]) VALUES (25, N'Запасник', N'Storage', 0, CAST(900.00 AS Decimal(10, 2)), N'+18°C', N'45%')
SET IDENTITY_INSERT [dbo].[HallsStorages] OFF
GO
SET IDENTITY_INSERT [dbo].[RestorationLogs] ON 

INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (1, 1, CAST(N'2023-05-15' AS Date), N'Реставрация лакового покрытия', CAST(45000.00 AS Decimal(18, 2)), N'Мастеров А.В.', CAST(N'2023-06-20' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (2, 2, CAST(N'2023-08-20' AS Date), N'Укрепление красочного слоя', CAST(120000.00 AS Decimal(18, 2)), N'Реставраторов Н.П.', CAST(N'2023-10-15' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (3, 3, CAST(N'2024-01-10' AS Date), N'Очистка поверхности', CAST(28000.00 AS Decimal(18, 2)), N'Мастеров А.В.', NULL, N'InProgress')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (4, 4, CAST(N'2023-11-05' AS Date), N'Восстановление фрагментов', CAST(85000.00 AS Decimal(18, 2)), N'Соколов Д.М.', CAST(N'2023-12-20' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (5, 5, CAST(N'2024-02-28' AS Date), N'Консервация', CAST(15000.00 AS Decimal(18, 2)), N'Реставраторов Н.П.', CAST(N'2024-03-15' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (6, 6, CAST(N'2023-09-12' AS Date), N'Замена подрамника', CAST(32000.00 AS Decimal(18, 2)), N'Мастеров А.В.', CAST(N'2023-10-01' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (7, 7, CAST(N'2024-03-01' AS Date), N'Химическая очистка', CAST(67000.00 AS Decimal(18, 2)), N'Петров С.И.', NULL, N'InProgress')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (8, 8, CAST(N'2023-12-18' AS Date), N'Ретушь утрат', CAST(41000.00 AS Decimal(18, 2)), N'Соколов Д.М.', CAST(N'2024-01-25' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (9, 9, CAST(N'2024-01-25' AS Date), N'Стабилизация основы', CAST(93000.00 AS Decimal(18, 2)), N'Реставраторов Н.П.', CAST(N'2024-03-10' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (10, 10, CAST(N'2023-10-30' AS Date), N'Профилактическая консервация', CAST(19000.00 AS Decimal(18, 2)), N'Мастеров А.В.', CAST(N'2023-11-15' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (11, 11, CAST(N'2023-04-10' AS Date), N'Восстановление основы', CAST(52000.00 AS Decimal(18, 2)), N'Петров С.И.', CAST(N'2023-05-20' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (12, 12, CAST(N'2023-07-22' AS Date), N'Укрепление грунта', CAST(38000.00 AS Decimal(18, 2)), N'Соколов Д.М.', CAST(N'2023-08-30' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (13, 13, CAST(N'2024-02-05' AS Date), N'Очистка от лака', CAST(75000.00 AS Decimal(18, 2)), N'Реставраторов Н.П.', CAST(N'2024-03-20' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (14, 14, CAST(N'2023-06-15' AS Date), N'Реставрация золочения', CAST(145000.00 AS Decimal(18, 2)), N'Мастеров А.В.', CAST(N'2023-08-10' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (15, 15, CAST(N'2023-09-28' AS Date), N'Восстановление живописи', CAST(62000.00 AS Decimal(18, 2)), N'Петров С.И.', CAST(N'2023-11-05' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (16, 16, CAST(N'2024-01-18' AS Date), N'Консервация дерева', CAST(48000.00 AS Decimal(18, 2)), N'Соколов Д.М.', NULL, N'InProgress')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (17, 17, CAST(N'2023-05-30' AS Date), N'Удаление загрязнений', CAST(22000.00 AS Decimal(18, 2)), N'Реставраторов Н.П.', CAST(N'2023-06-15' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (18, 18, CAST(N'2023-11-20' AS Date), N'Реставрация рамы', CAST(35000.00 AS Decimal(18, 2)), N'Мастеров А.В.', CAST(N'2023-12-10' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (19, 19, CAST(N'2024-03-05' AS Date), N'Укрепление слоя', CAST(58000.00 AS Decimal(18, 2)), N'Петров С.И.', NULL, N'InProgress')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (20, 20, CAST(N'2023-08-08' AS Date), N'Восстановление деталей', CAST(95000.00 AS Decimal(18, 2)), N'Соколов Д.М.', CAST(N'2023-10-20' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (21, 1, CAST(N'2023-10-12' AS Date), N'Химическая очистка', CAST(43000.00 AS Decimal(18, 2)), N'Реставраторов Н.П.', CAST(N'2023-11-25' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (22, 2, CAST(N'2024-02-14' AS Date), N'Реставрация холста', CAST(78000.00 AS Decimal(18, 2)), N'Мастеров А.В.', CAST(N'2024-04-01' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (23, 3, CAST(N'2023-07-05' AS Date), N'Консервация', CAST(25000.00 AS Decimal(18, 2)), N'Петров С.И.', CAST(N'2023-07-20' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (24, 4, CAST(N'2023-12-01' AS Date), N'Восстановление подписи', CAST(31000.00 AS Decimal(18, 2)), N'Соколов Д.М.', CAST(N'2023-12-28' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (25, 5, CAST(N'2024-01-30' AS Date), N'Реставрация грунта', CAST(88000.00 AS Decimal(18, 2)), N'Реставраторов Н.П.', NULL, N'InProgress')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (26, 6, CAST(N'2023-03-25' AS Date), N'Удаление реставраций', CAST(54000.00 AS Decimal(18, 2)), N'Мастеров А.В.', CAST(N'2023-05-10' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (27, 7, CAST(N'2023-09-18' AS Date), N'Стабилизация', CAST(47000.00 AS Decimal(18, 2)), N'Петров С.И.', CAST(N'2023-10-30' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (28, 8, CAST(N'2024-02-20' AS Date), N'Очистка и консервация', CAST(36000.00 AS Decimal(18, 2)), N'Соколов Д.М.', NULL, N'Cancelled')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (29, 9, CAST(N'2023-06-28' AS Date), N'Реставрация декора', CAST(69000.00 AS Decimal(18, 2)), N'Реставраторов Н.П.', CAST(N'2023-08-15' AS Date), N'Completed')
INSERT [dbo].[RestorationLogs] ([RestorationID], [ExhibitID], [RestorationDate], [Description], [Cost], [MasterName], [CompletionDate], [Status]) VALUES (30, 10, CAST(N'2024-03-10' AS Date), N'Комплексная реставрация', CAST(125000.00 AS Decimal(18, 2)), N'Мастеров А.В.', NULL, N'InProgress')
SET IDENTITY_INSERT [dbo].[RestorationLogs] OFF
GO
SET IDENTITY_INSERT [dbo].[Roles] ON 

INSERT [dbo].[Roles] ([RoleID], [RoleName], [Description], [CreatedDate]) VALUES (1, N'Администратор', N'Полный доступ ко всем функциям системы', CAST(N'2026-03-09T12:15:13.203' AS DateTime))
INSERT [dbo].[Roles] ([RoleID], [RoleName], [Description], [CreatedDate]) VALUES (2, N'Менеджер', N'Управление экспонатами и выставками', CAST(N'2026-03-09T12:15:13.203' AS DateTime))
INSERT [dbo].[Roles] ([RoleID], [RoleName], [Description], [CreatedDate]) VALUES (3, N'Пользователь', N'Только просмотр и отчеты', CAST(N'2026-03-09T12:15:13.203' AS DateTime))
SET IDENTITY_INSERT [dbo].[Roles] OFF
GO
SET IDENTITY_INSERT [dbo].[Users] ON 

INSERT [dbo].[Users] ([UserID], [Login], [PasswordHash], [FullName], [Email], [RoleID], [IsActive], [CreatedDate], [LastLogin]) VALUES (1, N'admin', N'hash_admin_123', N'Администратор Системы', N'admin@museum.ru', 1, 1, CAST(N'2026-03-09T12:15:13.207' AS DateTime), NULL)
INSERT [dbo].[Users] ([UserID], [Login], [PasswordHash], [FullName], [Email], [RoleID], [IsActive], [CreatedDate], [LastLogin]) VALUES (2, N'manager1', N'hash_mgr1_456', N'Петрова Мария Сергеевна', N'm.petrova@museum.ru', 2, 1, CAST(N'2026-03-09T12:15:13.207' AS DateTime), NULL)
INSERT [dbo].[Users] ([UserID], [Login], [PasswordHash], [FullName], [Email], [RoleID], [IsActive], [CreatedDate], [LastLogin]) VALUES (3, N'manager2', N'hash_mgr2_789', N'Сидоров Иван Петрович', N'i.sidorov@museum.ru', 2, 1, CAST(N'2026-03-09T12:15:13.207' AS DateTime), NULL)
INSERT [dbo].[Users] ([UserID], [Login], [PasswordHash], [FullName], [Email], [RoleID], [IsActive], [CreatedDate], [LastLogin]) VALUES (4, N'user1', N'hash_usr1_012', N'Козлов Дмитрий', N'd.kozlov@museum.ru', 3, 1, CAST(N'2026-03-09T12:15:13.207' AS DateTime), NULL)
INSERT [dbo].[Users] ([UserID], [Login], [PasswordHash], [FullName], [Email], [RoleID], [IsActive], [CreatedDate], [LastLogin]) VALUES (5, N'user2', N'hash_usr2_345', N'Новикова Ольга', N'o.novikova@museum.ru', 3, 1, CAST(N'2026-03-09T12:15:13.207' AS DateTime), NULL)
INSERT [dbo].[Users] ([UserID], [Login], [PasswordHash], [FullName], [Email], [RoleID], [IsActive], [CreatedDate], [LastLogin]) VALUES (6, N'guest', N'hash_guest_678', N'Гостевой доступ', N'guest@museum.ru', 3, 1, CAST(N'2026-03-09T12:15:13.207' AS DateTime), NULL)
SET IDENTITY_INSERT [dbo].[Users] OFF
GO
SET ANSI_PADDING ON
GO
/****** Object:  Index [UQ__Exhibits__D6D65CC882C4720A]    Script Date: 09.03.2026 12:21:51 ******/
ALTER TABLE [dbo].[Exhibitss] ADD UNIQUE NONCLUSTERED 
(
	[InventoryNumber] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, SORT_IN_TEMPDB = OFF, IGNORE_DUP_KEY = OFF, ONLINE = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
GO
SET ANSI_PADDING ON
GO
/****** Object:  Index [UQ__Roles__8A2B616007E7947F]    Script Date: 09.03.2026 12:21:51 ******/
ALTER TABLE [dbo].[Roles] ADD UNIQUE NONCLUSTERED 
(
	[RoleName] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, SORT_IN_TEMPDB = OFF, IGNORE_DUP_KEY = OFF, ONLINE = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
GO
SET ANSI_PADDING ON
GO
/****** Object:  Index [UQ__Users__5E55825BCE1C267B]    Script Date: 09.03.2026 12:21:51 ******/
ALTER TABLE [dbo].[Users] ADD UNIQUE NONCLUSTERED 
(
	[Login] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, SORT_IN_TEMPDB = OFF, IGNORE_DUP_KEY = OFF, ONLINE = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
GO
ALTER TABLE [dbo].[Roles] ADD  DEFAULT (getdate()) FOR [CreatedDate]
GO
ALTER TABLE [dbo].[Users] ADD  DEFAULT ((1)) FOR [IsActive]
GO
ALTER TABLE [dbo].[Users] ADD  DEFAULT (getdate()) FOR [CreatedDate]
GO
ALTER TABLE [dbo].[Exhibitss]  WITH CHECK ADD FOREIGN KEY([AdmissionHistoryID])
REFERENCES [dbo].[AdmissionHistory] ([AdmissionHistoryID])
GO
ALTER TABLE [dbo].[Exhibitss]  WITH CHECK ADD FOREIGN KEY([AuthorsCreatorsID])
REFERENCES [dbo].[AuthorsCreators] ([AuthorsCreatorsID])
GO
ALTER TABLE [dbo].[Exhibitss]  WITH CHECK ADD FOREIGN KEY([ExpositionsID])
REFERENCES [dbo].[Expositions] ([ExpositionsID])
GO
ALTER TABLE [dbo].[Exhibitss]  WITH CHECK ADD FOREIGN KEY([HallsStoragesID])
REFERENCES [dbo].[HallsStorages] ([HallsStoragesID])
GO
ALTER TABLE [dbo].[RestorationLogs]  WITH CHECK ADD FOREIGN KEY([ExhibitID])
REFERENCES [dbo].[Exhibitss] ([ExhibitsID])
GO
ALTER TABLE [dbo].[Users]  WITH CHECK ADD FOREIGN KEY([RoleID])
REFERENCES [dbo].[Roles] ([RoleID])
GO
USE [master]
GO
ALTER DATABASE [пр13] SET  READ_WRITE 
GO
