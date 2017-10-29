# dight_HZPT
数字杭科的API算法




	public static void main(String[] args) {
		//用户信息
		String str = "method=checkUserLoginIFS&idNumber=" + 2015002545 + "&UserPwd=" + "********" + "&logonIP="
				+ "115.193.237.242";
		//logonIP可以随机.反正是不判断的
		//用户盒子
		String str2 = "method=getMessageInBoxList&pageNo=" + 1 + "&userId=" + 2015002545 + "&idNumber="
				+ 1 + "&pageSize=10";
		String string = a(str2);
		System.out.println("http://i.hzpt.edu.cn/dcp/service?action=" + string);
		//其他的各种API.我就不一一搜索.自行去分析接口吧.
	}

	public static String a(String paramString) {
		try {
			Object localObject = new DESedeKeySpec("neusofteducationplatform".getBytes());
			localObject = SecretKeyFactory.getInstance("desede").generateSecret((KeySpec) localObject);
			Cipher localCipher = Cipher.getInstance("desede/CBC/PKCS5Padding");
			localCipher.init(1, (Key) localObject, new IvParameterSpec("01234567".getBytes()));
			byte[] bs = localCipher.doFinal(paramString.getBytes("utf-8"));
			System.out.println(bs.length);
			return byteToString(bs);
		} catch (Exception e) {
			e.printStackTrace();
		}
		return null;
	}

	private static String byteToString(byte[] paramArrayOfByte) {
		String str1 = "";
		for (int i = 0;; i++) {
			if (i >= paramArrayOfByte.length) {
				return str1;
			}
			String str3 = Integer.toHexString(paramArrayOfByte[i] & 0xFF);
			String str2 = str3;
			if (str3.length() == 1) {
				str2 = '0' + str3;
			}
			str1 = str1 + str2.toUpperCase();
		}
	}
