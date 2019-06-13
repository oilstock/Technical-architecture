public function access(){
			$rid = I('rid',0,'intval');
			$field = array('id','name','title','pid');
			$node = M('node')->field($field)->order('sort')->select();
			$access = M('access')->where(array('role_id'=>$rid))->getField('node_id',true);
			$node = node_merge($node,$access);
			$this->assign('node',$node);
			$this->assign('rid',$rid);
			$this->display();
