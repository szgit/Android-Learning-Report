## 代替TextWatcher进行两位小数的限制输入 ##

	/**
	 * 代替TextWatcher进行两位小数的限制输入
	 * @author didik
	 *
	 */
	public abstract class NumLimitWatcher implements TextWatcher{
	
		@Override
		public void beforeTextChanged(CharSequence s, int start, int count,
				int after) {
			
		}
	
		@Override
		public void onTextChanged(CharSequence s, int start, int before, int count) {
			
		}
	
		@Override
		public void afterTextChanged(Editable s) {
			if ("".equals(s.toString().trim())) {
				return;
			}
			if (!TextMoney.NumberLimited(s.toString().trim())) {
				int index=s.toString().length();
				s.delete(index-1, index);
			}
			afterTextChanged2(s);
		}
		
		protected abstract void afterTextChanged2(Editable s);
	
	}


用法:

	//do not delete those code
		mEt_commission.addTextChangedListener(new NumLimitWatcher() {
			
		@Override
		protected void afterTextChanged2(Editable s) {
		//do super
		doSomething();
		}
	});
			